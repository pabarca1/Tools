# Tools
Tools for Work
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Canned Responses</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Alexandria:wght@400;500;700&display=swap');
        body {
            font-family: 'Alexandria', sans-serif;
            background-color: #1f2937; /* Dark charcoal background */
            color: #e5e7eb; /* Light gray text */
        }
        .message-box {
            position: fixed;
            top: 20px;
            right: 20px;
            z-index: 1000;
            padding: 1rem;
            border-radius: 0.5rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            color: white;
            transition: opacity 0.5s ease-in-out;
            opacity: 0;
            pointer-events: none;
        }
        .message-box.show {
            opacity: 1;
        }
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1001;
        }
        .modal-content {
            background-color: #374151; /* Slightly lighter dark gray for contrast */
            color: #e5e7eb;
            padding: 2rem;
            border-radius: 0.5rem;
            box-shadow: 0 10px 15px rgba(0, 0, 0, 0.2);
            width: 90%;
            max-width: 400px;
        }
        .scrollbar-hide::-webkit-scrollbar {
            display: none;
        }
        .scrollbar-hide {
            -ms-overflow-style: none;
            scrollbar-width: none;
        }
        .sidebar {
            position: fixed;
            top: 0;
            left: -256px; /* Hidden by default */
            width: 256px;
            height: 100%;
            background-color: #1f2937;
            padding: 2rem 1rem;
            box-shadow: 2px 0 5px rgba(0,0,0,0.1);
            transition: left 0.3s ease-in-out;
            z-index: 2000;
        }
        .sidebar.open {
            left: 0;
        }
    </style>
</head>
<body class="flex flex-col min-h-screen bg-gray-900 relative">

    <!-- Sidebar -->
    <div id="sidebar" class="sidebar flex flex-col">
        <h2 class="text-2xl font-bold text-gray-200 mb-6">Tools</h2>
        <nav class="flex flex-col space-y-2">
            <button id="nav-canned-responses" class="w-full text-left px-4 py-2 rounded-lg hover:bg-gray-700 transition text-gray-200 font-semibold">Canned Responses</button>
            <button id="nav-fedex-tracker" class="w-full text-left px-4 py-2 rounded-lg hover:bg-gray-700 transition text-gray-200 font-semibold">FedEx Tracker</button>
        </nav>
        <button id="close-sidebar-btn" class="absolute top-4 right-4 p-2 rounded-full hover:bg-gray-700 transition">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
            </svg>
        </button>
    </div>

    <!-- Main Content -->
    <div id="main-content" class="flex-1 p-4 sm:p-8 flex flex-col items-center">
        <header class="w-full max-w-2xl flex items-center justify-between mb-6">
            <div class="flex items-center space-x-2">
                <button id="hamburger-menu-btn" class="p-2 rounded-full hover:bg-gray-700 transition" aria-label="Open Menu">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
                    </svg>
                </button>
                <h1 id="main-title" class="text-3xl sm:text-4xl font-bold text-gray-200">Canned Responses</h1>
                <div class="relative">
                    <button id="category-menu-btn" class="p-2 rounded-full hover:bg-gray-700 transition" aria-label="Category Menu">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M12 5v.01M12 12v.01M12 19v.01M12 6a1 1 0 110-2 1 1 0 010 2zm0 7a1 1 0 110-2 1 1 0 010 2zm0 7a1 1 0 110-2 1 1 0 010 2z" />
                        </svg>
                    </button>
                    <div id="category-menu" class="absolute top-full left-0 mt-2 w-48 bg-gray-700 rounded-lg shadow-lg z-50 hidden">
                        <button id="rename-category-btn" class="w-full text-left px-4 py-2 hover:bg-gray-600 rounded-t-lg">Rename Category</button>
                        <button id="delete-category-btn" class="w-full text-left px-4 py-2 hover:bg-gray-600 text-red-400">Delete Category</button>
                        <button id="change-color-btn" class="w-full text-left px-4 py-2 hover:bg-gray-600 rounded-b-lg">Change Color</button>
                    </div>
                </div>
            </div>
            <div class="flex items-center space-x-2">
                <button id="import-export-btn" class="text-gray-400 hover:text-blue-400 transition" aria-label="Import/Export Data">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-8l-4-4m0 0L8 8m4-4v12" />
                    </svg>
                </button>
            </div>
        </header>

        <!-- Message box for user feedback -->
        <div id="message-box" class="message-box"></div>

        <!-- Canned Responses App Content -->
        <div id="canned-responses-app" class="w-full max-w-2xl bg-gray-800 rounded-xl shadow-lg p-6 sm:p-8">
            <!-- Search Bar -->
            <div id="search-bar-container" class="mb-6 relative hidden">
                <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
                    </svg>
                </div>
                <input
                    type="text"
                    id="search-input"
                    class="w-full border border-gray-600 rounded-lg p-3 pl-10 bg-gray-700 text-gray-200 focus:outline-none focus:ring-2 focus:ring-blue-500 transition"
                    placeholder="Search responses..."
                />
            </div>
            
            <!-- Add Response Section -->
            <div id="add-response-section" class="mb-8">
                <label for="response-input" class="block text-gray-400 font-semibold mb-2">Add New Response</label>
                <div class="flex flex-col sm:flex-row gap-4 mb-4">
                    <textarea
                        id="response-input"
                        class="flex-grow w-full border border-gray-600 rounded-lg p-3 bg-gray-700 text-gray-200 focus:outline-none focus:ring-2 focus:ring-blue-500 transition"
                        rows="5"
                        placeholder="Type your new canned response here..."
                    ></textarea>
                </div>
                <div class="flex flex-col sm:flex-row gap-4 items-center">
                    <button id="add-btn" class="w-full sm:w-auto bg-blue-600 text-white font-bold py-3 px-6 rounded-lg shadow-md hover:bg-blue-700 transition">
                        Add Response
                    </button>
                </div>
            </div>

            <!-- Responses List -->
            <div id="responses-container">
                <h2 id="responses-heading" class="text-2xl font-bold text-gray-200 mb-4 hidden"></h2>
                
                <div id="responses-list" class="space-y-6">
                    <!-- Responses will be dynamically added here, grouped by label -->
                </div>
                <div id="empty-state" class="text-center text-gray-400 mt-8 hidden">
                    <p>No canned responses in this category. Add one above!</p>
                </div>
            </div>
        </div>

        <!-- FedEx Tracker Content -->
        <div id="fedex-tracker-app" class="w-full max-w-2xl bg-gray-800 rounded-xl shadow-lg p-6 sm:p-8 hidden">
            <h1 class="text-3xl font-bold text-gray-200 mb-6 text-center">FedEx Tracking Number Separator</h1>
            <p class="text-gray-400 mb-6 text-center">
                Paste your text below and the program will extract the tracking numbers.
            </p>
        
            <textarea id="fedex-input-text" rows="10"
                            class="w-full px-4 py-2 border border-gray-600 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 transition-all bg-gray-700 text-gray-200"
                            placeholder="e.g.,
Hello, this is a message about some packages.
The tracking numbers are 784381023758 and 784381023759.
Another number is here: 123-456-789-012 but that's not a valid length.
Here is a third tracking number: 784381023760. And another: 784381023761
Please disregard all the other information on this page."></textarea>
        
            <button id="fedex-extract-btn"
                        class="w-full bg-blue-600 text-white font-semibold py-3 rounded-lg hover:bg-blue-700 transition-colors focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 mt-4">
                Extract Tracking Numbers
            </button>
        
            <div class="mt-8">
                <label class="block text-sm font-medium text-gray-400 mb-2">
                    Extracted Numbers (with tabs)
                </label>
                <textarea id="fedex-output-area" rows="5" readonly
                            class="w-full px-4 py-2 border border-gray-600 rounded-lg bg-gray-700 text-gray-200 font-mono"></textarea>
                <button id="fedex-copy-btn"
                            class="mt-2 w-full bg-green-500 text-white font-semibold py-2 rounded-lg hover:bg-green-600 transition-colors focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-offset-2">
                    Copy to Clipboard
                </button>
            </div>
        </div>
    </div>

    <!-- Floating Category Bar at the bottom -->
    <div id="category-bar" class="fixed bottom-0 left-0 right-0 p-4 sm:p-6 bg-gray-800 shadow-xl flex items-center justify-between z-40">
        <div class="flex-grow overflow-x-auto whitespace-nowrap scrollbar-hide">
            <div id="category-list" class="flex gap-4">
                <!-- Category buttons will be dynamically added here -->
            </div>
        </div>
        <button id="add-category-btn" class="flex-shrink-0 ml-4 bg-blue-500 text-white font-bold py-2 px-4 rounded-lg shadow-md hover:bg-blue-600 transition">
            +
        </button>
    </div>

    <!-- Import/Export Modal -->
    <div id="import-export-modal" class="modal hidden">
        <div class="modal-content">
            <h3 class="text-xl font-bold text-gray-200 mb-4">Import or Export Data</h3>
            <div class="flex flex-col space-y-4">
                <div>
                    <h4 class="font-semibold text-gray-400">Export All Data</h4>
                    <p class="text-gray-400 text-sm mb-2">Download a JSON file containing all your categories and responses.</p>
                    <button id="export-btn" class="w-full bg-blue-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-blue-700 transition">
                        Export to File
                    </button>
                </div>
                <div>
                    <h4 class="font-semibold text-gray-400">Import Data</h4>
                    <p class="text-gray-400 text-sm mb-2">Upload a JSON file to restore your categories and responses. This will overwrite your current data.</p>
                    <input type="file" id="import-file-input" accept="application/json" class="w-full border border-gray-600 rounded-lg p-2 bg-gray-700 text-gray-200 transition">
                </div>
            </div>
            <div class="flex justify-end mt-6">
                <button id="close-import-export-modal-btn" class="bg-gray-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-gray-700 transition">
                    Close
                </button>
            </div>
        </div>
    </div>

    <!-- Add Category Modal -->
    <div id="add-category-modal" class="modal hidden">
        <div class="modal-content">
            <h3 class="text-xl font-bold text-gray-200 mb-4">Add a New Category</h3>
            <p class="text-gray-400 mb-4">Give your new category a name.</p>
            <input
                type="text"
                id="add-category-input"
                class="w-full border border-gray-600 rounded-lg p-3 bg-gray-700 text-gray-200 focus:outline-none focus:ring-2 focus:ring-blue-500 transition mb-4"
                placeholder="Enter category name (e.g., 'Customer Support')"
            />
            <div class="flex justify-end space-x-4">
                <button id="cancel-add-category-btn" class="bg-gray-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-gray-700 transition">
                    Cancel
                </button>
                <button id="confirm-add-category-btn" class="bg-blue-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-blue-700 transition">
                    Create Category
                </button>
            </div>
        </div>
    </div>

    <!-- Edit Category Modal -->
    <div id="edit-category-modal" class="modal hidden">
        <div class="modal-content">
            <h3 class="text-xl font-bold text-gray-200 mb-4">Edit Category</h3>
            <p class="text-gray-400 mb-4">Enter a new name for the category.</p>
            <input
                type="text"
                id="edit-category-input"
                class="w-full border border-gray-600 rounded-lg p-3 bg-gray-700 text-gray-200 focus:outline-none focus:ring-2 focus:ring-blue-500 transition mb-4"
                placeholder="Enter new name"
            />
            <div class="flex justify-end space-x-4">
                <button id="cancel-edit-category-btn" class="bg-gray-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-gray-700 transition">
                    Cancel
                </button>
                <button id="confirm-edit-category-btn" class="bg-blue-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-blue-700 transition">
                    Save Name
                </button>
            </div>
        </div>
    </div>

    <!-- Delete Category Modal -->
    <div id="delete-category-modal" class="modal hidden">
        <div class="modal-content">
            <h3 class="text-xl font-bold text-gray-200 mb-4">Confirm Category Deletion</h3>
            <p class="text-gray-400 mb-4">Are you sure you want to delete this category? All responses inside it will be permanently deleted.</p>
            <div class="flex justify-end space-x-4">
                <button id="cancel-delete-category-btn" class="bg-gray-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-gray-700 transition">
                    Cancel
                </button>
                <button id="confirm-delete-category-btn" class="bg-red-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-red-700 transition">
                    Yes, Delete
                </button>
            </div>
        </div>
    </div>

    <!-- Color Picker Modal -->
    <div id="color-picker-modal" class="modal hidden">
        <div class="modal-content">
            <h3 class="text-xl font-bold text-gray-200 mb-4">Change Category Color</h3>
            <p class="text-gray-400 mb-4">Select a new color for the active category.</p>
            <div class="flex justify-center mb-4">
                <input type="color" id="color-input" class="w-16 h-16 cursor-pointer">
            </div>
            <div class="flex justify-end mt-6">
                <button id="close-color-picker-btn" class="bg-gray-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-gray-700 transition">
                    Close
                </button>
                <button id="save-color-btn" class="bg-blue-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-blue-700 transition">
                    Save
                </button>
            </div>
        </div>
    </div>


    <!-- Label Modal -->
    <div id="label-modal" class="modal hidden">
        <div class="modal-content">
            <h3 class="text-xl font-bold text-gray-200 mb-4">Add a Label</h3>
            <p class="text-gray-400 mb-4">Give your new response a label to help keep things organized.</p>
            <input
                type="text"
                id="modal-label-input"
                class="w-full border border-gray-600 rounded-lg p-3 bg-gray-700 text-gray-200 focus:outline-none focus:ring-2 focus:ring-blue-500 transition mb-4"
                placeholder="Enter a label (e.g., 'Customer Support')"
            />
            <div class="flex justify-end space-x-4">
                <button id="cancel-label-btn" class="bg-gray-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-gray-700 transition">
                    Cancel
                </button>
                <button id="save-label-btn" class="bg-blue-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-blue-700 transition">
                    Save Label
                </button>
            </div>
        </div>
    </div>

    <!-- Delete Confirmation Modal -->
    <div id="delete-modal" class="modal hidden">
        <div class="modal-content">
            <h3 class="text-xl font-bold text-gray-200 mb-4">Confirm Deletion</h3>
            <p class="text-gray-400 mb-4">Are you sure you want to delete this response?</p>
            <div class="flex justify-end space-x-4">
                <button id="delete-cancel-btn" class="bg-gray-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-gray-700 transition">
                    Cancel
                </button>
                <button id="delete-confirm-btn" class="bg-red-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-red-700 transition">
                    Yes, Delete
                </button>
            </div>
        </div>
    </div>

    <script>
        const saveToLocalStorage = () => {
            localStorage.setItem('categories', JSON.stringify(categories));
            localStorage.setItem('activeCategory', activeCategory);
        };

        const renderContent = () => {
            const cannedResponsesApp = document.getElementById('canned-responses-app');
            const fedexTrackerApp = document.getElementById('fedex-tracker-app');
            const categoryBar = document.getElementById('category-bar');

            if (currentPage === 'canned-responses') {
                cannedResponsesApp.classList.remove('hidden');
                categoryBar.classList.remove('hidden');
                fedexTrackerApp.classList.add('hidden');
                renderCategories();
            } else if (currentPage === 'fedex-tracker') {
                cannedResponsesApp.classList.add('hidden');
                categoryBar.classList.add('hidden');
                fedexTrackerApp.classList.remove('hidden');
                document.title = 'FedEx Tracker';
                mainTitle.textContent = 'FedEx Tracker';
            }
        };

        let categories = JSON.parse(localStorage.getItem('categories')) || {};
        let activeCategory = localStorage.getItem('activeCategory') || 'Uncategorized';
        let newResponseId = null;
        let responseToDeleteId = null;
        let categoryToEdit = null;
        let newCategoryName = null;
        let currentPage = localStorage.getItem('currentPage') || 'canned-responses';

        if (!categories['Uncategorized']) {
            categories['Uncategorized'] = { color: '#60a5fa', responses: [] }; // Initialized with a default color
            saveToLocalStorage();
        }

        const responseInput = document.getElementById('response-input');
        const addBtn = document.getElementById('add-btn');
        const responsesList = document.getElementById('responses-list');
        const emptyState = document.getElementById('empty-state');
        const messageBox = document.getElementById('message-box');
        const labelModal = document.getElementById('label-modal');
        const modalLabelInput = document.getElementById('modal-label-input');
        const saveLabelBtn = document.getElementById('save-label-btn');
        const cancelLabelBtn = document.getElementById('cancel-label-btn');
        const deleteModal = document.getElementById('delete-modal');
        const deleteConfirmBtn = document.getElementById('delete-confirm-btn');
        const deleteCancelBtn = document.getElementById('delete-cancel-btn');
        const categoryList = document.getElementById('category-list');
        const addCategoryBtn = document.getElementById('add-category-btn');
        const addCategoryModal = document.getElementById('add-category-modal');
        const addCategoryInput = document.getElementById('add-category-input');
        const confirmAddCategoryBtn = document.getElementById('confirm-add-category-btn');
        const cancelAddCategoryBtn = document.getElementById('cancel-add-category-btn');
        const noCategoriesMessage = document.getElementById('no-categories-message');
        const addResponseSection = document.getElementById('add-response-section');
        const responsesHeading = document.getElementById('responses-heading');
        const mainTitle = document.getElementById('main-title');

        const importExportBtn = document.getElementById('import-export-btn');
        const importExportModal = document.getElementById('import-export-modal');
        const exportBtn = document.getElementById('export-btn');
        const importFileInput = document.getElementById('import-file-input');
        const closeImportExportModalBtn = document.getElementById('close-import-export-modal-btn');
        
        const searchInput = document.getElementById('search-input');
        const searchBarContainer = document.getElementById('search-bar-container');

        const editCategoryModal = document.getElementById('edit-category-modal');
        const editCategoryInput = document.getElementById('edit-category-input');
        const confirmEditCategoryBtn = document.getElementById('confirm-edit-category-btn');
        const cancelEditCategoryBtn = document.getElementById('cancel-edit-category-btn');
        const deleteCategoryModal = document.getElementById('delete-category-modal');
        const confirmDeleteCategoryBtn = document.getElementById('confirm-delete-category-btn');
        const cancelDeleteCategoryBtn = document.getElementById('cancel-delete-category-btn');

        const categoryMenuBtn = document.getElementById('category-menu-btn');
        const categoryMenu = document.getElementById('category-menu');
        const renameCategoryBtn = document.getElementById('rename-category-btn');
        const deleteCategoryBtn = document.getElementById('delete-category-btn');
        const changeColorBtn = document.getElementById('change-color-btn');

        const colorPickerModal = document.getElementById('color-picker-modal');
        const colorInput = document.getElementById('color-input');
        const closeColorPickerBtn = document.getElementById('close-color-picker-btn');
        const saveColorBtn = document.getElementById('save-color-btn');

        const hamburgerMenuBtn = document.getElementById('hamburger-menu-btn');
        const sidebar = document.getElementById('sidebar');
        const closeSidebarBtn = document.getElementById('close-sidebar-btn');
        const navCannedResponses = document.getElementById('nav-canned-responses');
        const navFedexTracker = document.getElementById('nav-fedex-tracker');

        const fedexInputText = document.getElementById('fedex-input-text');
        const fedexExtractBtn = document.getElementById('fedex-extract-btn');
        const fedexOutputArea = document.getElementById('fedex-output-area');
        const fedexCopyBtn = document.getElementById('fedex-copy-btn');
        
        const showMessage = (text, type = 'success') => {
            messageBox.textContent = text;
            messageBox.className = 'message-box show';
            if (type === 'success') {
                messageBox.style.backgroundColor = '#10B981';
            } else if (type === 'error') {
                messageBox.style.backgroundColor = '#EF4444';
            }
            setTimeout(() => {
                messageBox.className = 'message-box';
            }, 3000);
        };
        
        const renderCategories = () => {
            categoryList.innerHTML = '';
            const categoryNames = Object.keys(categories);
            if (categoryNames.length === 0) {
                if (!categories['Uncategorized']) {
                    categories['Uncategorized'] = { color: '#60a5fa', responses: [] };
                    saveToLocalStorage();
                }
                activeCategory = 'Uncategorized';
                renderCategories();
                return;
            }

            addResponseSection.classList.remove('hidden');
            searchBarContainer.classList.remove('hidden');
            
            categoryNames.forEach(name => {
                const button = document.createElement('div');
                button.className = `category-item-container flex items-center relative`;
                const isSelected = name === activeCategory;
                const categoryData = categories[name];
                
                const buttonColor = categoryData.color || '#60a5fa';

                button.innerHTML = `
                    <button class="category-item font-bold py-2 px-4 rounded-lg shadow-md text-white transition-colors
                        ${isSelected ? 'border-2 border-white' : ''}"
                        style="background-color: ${buttonColor};"
                        data-category="${name}">
                        ${name}
                    </button>
                `;
                categoryList.appendChild(button);
            });
            
            if (!categories[activeCategory]) {
                activeCategory = categoryNames[0];
            }
            renderResponses();
        };

        const renderResponses = (searchQuery = '') => {
            responsesList.innerHTML = '';
            
            if (activeCategory === 'Uncategorized') {
                document.title = 'Canned Responses';
                mainTitle.textContent = 'Canned Responses';
                responsesHeading.classList.remove('hidden');
                responsesHeading.textContent = `Responses in: Uncategorized`;
                categoryMenuBtn.classList.add('hidden');
            } else if (activeCategory) {
                document.title = `${activeCategory} - Canned Responses`;
                mainTitle.textContent = activeCategory;
                responsesHeading.classList.remove('hidden');
                responsesHeading.textContent = `Responses in: ${activeCategory}`;
                categoryMenuBtn.classList.remove('hidden');
            } else {
                document.title = 'Canned Responses';
                mainTitle.textContent = 'Canned Responses';
                responsesHeading.classList.add('hidden');
                categoryMenuBtn.classList.add('hidden');
                return;
            }

            let responses = categories[activeCategory] ? categories[activeCategory].responses : [];
            if (responses) {
                if (searchQuery) {
                    const query = searchQuery.toLowerCase();
                    responses = responses.filter(r => 
                        (r.text && r.text.toLowerCase().includes(query)) ||
                        (r.label && r.label.toLowerCase().includes(query))
                    );
                }
            } else {
                responses = [];
            }


            if (responses.length > 0) {
                emptyState.classList.add('hidden');
                const groupedResponses = responses.reduce((acc, response) => {
                    const label = response.label || 'Unlabeled';
                    if (!acc[label]) {
                        acc[label] = [];
                    }
                    acc[label].push(response);
                    return acc;
                }, {});

                for (const label in groupedResponses) {
                    const labelSection = document.createElement('div');
                    labelSection.className = 'mb-6';
                    labelSection.innerHTML = `
                        <h3 class="text-xl font-bold text-gray-400 mb-2">${label}</h3>
                        <div class="space-y-4"></div>
                    `;
                    const responsesInSection = labelSection.querySelector('div');

                    groupedResponses[label].forEach(response => {
                        const responseEl = document.createElement('div');
                        responseEl.className = 'response-item flex flex-col sm:flex-row items-start sm:items-center justify-between bg-gray-700 p-4 rounded-lg border border-gray-600';
                        responseEl.dataset.id = response.id;

                        const displayHTML = `
                            <div class="flex-grow display-mode">
                                <p class="response-text text-gray-200 mb-2 sm:mb-0 sm:mr-4 whitespace-pre-wrap">${response.text}</p>
                                <div class="flex-shrink-0 flex space-x-2 mt-2 sm:mt-0">
                                    <button class="copy-btn bg-green-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-green-700 transition">
                                        Copy
                                    </button>
                                    <button class="edit-btn bg-yellow-500 text-white font-bold py-2 px-4 rounded-lg hover:bg-yellow-600 transition">
                                        Edit
                                    </button>
                                    <button class="delete-btn bg-red-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-red-700 transition">
                                        Delete
                                    </button>
                                </div>
                            </div>
                        `;

                        const categoryOptions = Object.keys(categories).map(cat => `<option value="${cat}" ${cat === activeCategory ? 'selected' : ''}>${cat}</option>`).join('');

                        const editHTML = `
                            <div class="flex-grow edit-mode hidden">
                                <div class="flex flex-col space-y-2">
                                    <textarea class="edit-response-input w-full border border-gray-600 rounded-lg p-2 bg-gray-700 text-gray-200 focus:outline-none focus:ring-2 focus:ring-blue-500 transition" rows="3">${response.text}</textarea>
                                    <input type="text" class="edit-label-input w-full border border-gray-600 rounded-lg p-2 bg-gray-700 text-gray-200" value="${response.label || ''}">
                                    <select class="edit-category-select w-full border border-gray-600 rounded-lg p-2 bg-gray-700 text-gray-200 focus:outline-none focus:ring-2 focus:ring-blue-500 transition">
                                        ${categoryOptions}
                                    </select>
                                </div>
                                <div class="flex-shrink-0 flex space-x-2 mt-2 sm:mt-0">
                                    <button class="save-btn bg-blue-600 text-white font-bold py-2 px-4 rounded-lg shadow-md hover:bg-blue-700 transition">
                                        Save
                                    </button>
                                    <button class="cancel-btn bg-gray-500 text-white font-bold py-2 px-4 rounded-lg shadow-md hover:bg-gray-600 transition">
                                        Cancel
                                    </button>
                                </div>
                            </div>
                        `;

                        responseEl.innerHTML = displayHTML + editHTML;
                        responsesInSection.appendChild(responseEl);
                    });
                    responsesList.appendChild(labelSection);
                }
            } else {
                emptyState.classList.remove('hidden');
            }
        };

        const addResponse = (text) => {
            if (!text.trim()) {
                showMessage("Please enter a response to save.", 'error');
                return;
            }

            if (!activeCategory) {
                showMessage("Please create or select a category first.", 'error');
                return;
            }

            const newId = Date.now().toString();
            const newResponse = { id: newId, text: text, label: '', createdAt: new Date().toISOString() };
            categories[activeCategory].responses.push(newResponse);
            saveToLocalStorage();
            responseInput.value = '';
            newResponseId = newId;
            labelModal.classList.remove('hidden');
            modalLabelInput.focus();
        };

        const updateResponse = (id, newText, newLabel, newCategory) => {
            const oldCategory = activeCategory;
            const responsesInOldCategory = categories[oldCategory].responses;
            const responseIndex = responsesInOldCategory.findIndex(r => r.id === id);
            
            if (responseIndex > -1) {
                const responseToUpdate = responsesInOldCategory[responseIndex];
                responseToUpdate.text = newText;
                responseToUpdate.label = newLabel || '';
                
                if (newCategory && newCategory !== oldCategory) {
                    responsesInOldCategory.splice(responseIndex, 1);
                    if (!categories[newCategory]) {
                         categories[newCategory] = { color: '#60a5fa', responses: [] };
                    }
                    categories[newCategory].responses.push(responseToUpdate);
                    activeCategory = newCategory;
                    renderCategories();
                }

                saveToLocalStorage();
                showMessage("Response updated successfully!");
                renderResponses();
            }
        };

        const deleteResponse = (id) => {
            if (!activeCategory) return;

            categories[activeCategory].responses = categories[activeCategory].responses.filter(r => r.id !== id);
            saveToLocalStorage();
            renderResponses();
            showMessage("Response deleted successfully!");
        };

        const copyToClipboard = (text) => {
            const el = document.createElement('textarea');
            el.value = text;
            document.body.appendChild(el);
            el.select();
            document.execCommand('copy');
            document.body.removeChild(el);
            showMessage("Copied to clipboard!");
        };

        const exportData = () => {
            const dataStr = JSON.stringify(categories, null, 2);
            const blob = new Blob([dataStr], { type: 'application/json' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'canned_responses.json';
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
            showMessage("Data exported successfully!");
        };

        const importData = (file) => {
            const reader = new FileReader();
            reader.onload = (e) => {
                try {
                    const importedData = JSON.parse(e.target.result);
                    if (typeof importedData === 'object' && importedData !== null) {
                        categories = importedData;
                        const categoryNames = Object.keys(categories);
                        if (categoryNames.length > 0) {
                            activeCategory = categoryNames[0];
                        } else {
                            activeCategory = 'Uncategorized';
                            categories['Uncategorized'] = { color: '#60a5fa', responses: [] };
                        }
                        saveToLocalStorage();
                        renderCategories();
                        showMessage("Data imported successfully!");
                        importExportModal.classList.add('hidden');
                    } else {
                        throw new Error('Invalid JSON format.');
                    }
                } catch (error) {
                    showMessage(`Error importing file: ${error.message}`, 'error');
                }
            };
            reader.readAsText(file);
        };

        const trackingNumberRegex = /[a-zA-Z0-9]{12,22}/g;
        
        function extractAndFormat(inputText) {
            const matches = inputText.match(trackingNumberRegex);
            if (!matches) {
                return "";
            }
            return matches.join("\t");
        }

        // --- Event Listeners ---
        hamburgerMenuBtn.addEventListener('click', () => {
            sidebar.classList.add('open');
        });

        closeSidebarBtn.addEventListener('click', () => {
            sidebar.classList.remove('open');
        });

        navCannedResponses.addEventListener('click', () => {
            currentPage = 'canned-responses';
            localStorage.setItem('currentPage', currentPage);
            renderContent();
            sidebar.classList.remove('open');
        });

        navFedexTracker.addEventListener('click', () => {
            currentPage = 'fedex-tracker';
            localStorage.setItem('currentPage', currentPage);
            renderContent();
            sidebar.classList.remove('open');
        });

        fedexExtractBtn.addEventListener('click', () => {
            const inputText = fedexInputText.value;
            const outputText = extractAndFormat(inputText);
            fedexOutputArea.value = outputText;
        });

        fedexCopyBtn.addEventListener('click', () => {
            fedexOutputArea.select();
            document.execCommand('copy');
            showMessage("Copied to clipboard!");
        });


        importExportBtn.addEventListener('click', () => {
            importExportModal.classList.remove('hidden');
        });
        closeImportExportModalBtn.addEventListener('click', () => {
            importExportModal.classList.add('hidden');
        });
        exportBtn.addEventListener('click', exportData);
        importFileInput.addEventListener('change', (event) => {
            const file = event.target.files[0];
            if (file) {
                importData(file);
            }
        });

        addCategoryBtn.addEventListener('click', () => {
            addCategoryModal.classList.remove('hidden');
            addCategoryInput.focus();
        });

        confirmAddCategoryBtn.addEventListener('click', () => {
            const categoryName = addCategoryInput.value.trim();
            if (!categoryName) {
                showMessage("Please enter a category name.", 'error');
                return;
            }
            if (categories[categoryName]) {
                showMessage("A category with this name already exists.", 'error');
                return;
            }
            
            categories[categoryName] = { color: '#60a5fa', responses: [] };
            activeCategory = categoryName;
            addCategoryModal.classList.add('hidden');
            saveToLocalStorage();
            renderCategories();
            showMessage(`Category '${categoryName}' created successfully!`);
        });

        cancelAddCategoryBtn.addEventListener('click', () => {
            addCategoryInput.value = '';
            addCategoryModal.classList.add('hidden');
        });
        
        categoryList.addEventListener('click', (event) => {
            const target = event.target;
            const itemBtn = target.closest('.category-item');
            
            if (itemBtn) {
                const categoryName = itemBtn.dataset.category;
                if (categoryName !== activeCategory) {
                    activeCategory = categoryName;
                    renderCategories();
                    renderResponses();
                }
            }
        });

        // Event listeners for the new header menu
        categoryMenuBtn.addEventListener('click', () => {
            categoryMenu.classList.toggle('hidden');
        });

        renameCategoryBtn.addEventListener('click', () => {
            categoryToEdit = activeCategory;
            editCategoryInput.value = categoryToEdit;
            editCategoryModal.classList.remove('hidden');
            categoryMenu.classList.add('hidden');
        });

        deleteCategoryBtn.addEventListener('click', () => {
            categoryToEdit = activeCategory;
            deleteCategoryModal.classList.remove('hidden');
            categoryMenu.classList.add('hidden');
        });

        changeColorBtn.addEventListener('click', () => {
            if (activeCategory && activeCategory !== 'Uncategorized') {
                const currentColor = categories[activeCategory].color || '#60a5fa';
                colorInput.value = currentColor;
                colorPickerModal.classList.remove('hidden');
                categoryMenu.classList.add('hidden');
            } else {
                showMessage("You can't change the color of the 'Uncategorized' category.", 'error');
            }
        });
        
        saveColorBtn.addEventListener('click', () => {
            const newColor = colorInput.value;
            if (activeCategory) {
                categories[activeCategory].color = newColor;
                saveToLocalStorage();
                renderCategories();
                showMessage(`Color for '${activeCategory}' changed successfully!`);
            }
            colorPickerModal.classList.add('hidden');
        });


        closeColorPickerBtn.addEventListener('click', () => {
            colorPickerModal.classList.add('hidden');
        });

        document.addEventListener('click', (event) => {
            if (!event.target.closest('#category-menu-btn') && !event.target.closest('#category-menu')) {
                categoryMenu.classList.add('hidden');
            }
        });


        confirmEditCategoryBtn.addEventListener('click', () => {
            const newName = editCategoryInput.value.trim();
            if (!newName) {
                showMessage("Category name cannot be empty.", 'error');
                return;
            }
            if (newName === categoryToEdit) {
                editCategoryModal.classList.add('hidden');
                return;
            }
            if (categories[newName]) {
                showMessage("A category with this name already exists.", 'error');
                return;
            }
            
            categories[newName] = categories[categoryToEdit];
            delete categories[categoryToEdit];
            if (activeCategory === categoryToEdit) {
                activeCategory = newName;
            }
            categoryToEdit = null;
            saveToLocalStorage();
            editCategoryModal.classList.add('hidden');
            renderCategories();
        });

        cancelEditCategoryBtn.addEventListener('click', () => {
            categoryToEdit = null;
            editCategoryModal.classList.add('hidden');
        });

        confirmDeleteCategoryBtn.addEventListener('click', () => {
            if (categoryToEdit) {
                delete categories[categoryToEdit];
                if (activeCategory === categoryToEdit) {
                    const categoryNames = Object.keys(categories);
                    activeCategory = categoryNames.length > 0 ? categoryNames[0] : 'Uncategorized';
                }
                categoryToEdit = null;
                saveToLocalStorage();
                deleteCategoryModal.classList.add('hidden');
                renderCategories();
                showMessage("Category deleted successfully!");
            }
        });

        cancelDeleteCategoryBtn.addEventListener('click', () => {
            categoryToEdit = null;
            deleteCategoryModal.classList.add('hidden');
        });

        addBtn.addEventListener('click', () => {
            addResponse(responseInput.value);
        });

        responsesList.addEventListener('click', (event) => {
            const target = event.target;
            const parentEl = target.closest('.response-item');
            if (!parentEl) return;
            const id = parentEl.dataset.id;
            
            const displayMode = parentEl.querySelector('.display-mode');
            const editMode = parentEl.querySelector('.edit-mode');
            
            if (target.classList.contains('copy-btn')) {
                const responses = categories[activeCategory].responses;
                const text = responses.find(r => r.id === id).text;
                copyToClipboard(text);
            } else if (target.classList.contains('edit-btn')) {
                displayMode.classList.add('hidden');
                editMode.classList.remove('hidden');
            } else if (target.classList.contains('save-btn')) {
                const newText = parentEl.querySelector('.edit-response-input').value;
                const newLabel = parentEl.querySelector('.edit-label-input').value;
                const newCategory = parentEl.querySelector('.edit-category-select').value;
                
                updateResponse(id, newText, newLabel, newCategory);

            } else if (target.classList.contains('cancel-btn')) {
                const responses = categories[activeCategory].responses;
                const response = responses.find(r => r.id === id);
                if (response) {
                    parentEl.querySelector('.edit-response-input').value = response.text;
                    parentEl.querySelector('.edit-label-input').value = response.label || '';
                }
                displayMode.classList.remove('hidden');
                editMode.classList.add('hidden');
            } else if (target.classList.contains('delete-btn')) {
                responseToDeleteId = id;
                deleteModal.classList.remove('hidden');
            }
        });

        // Search functionality
        searchInput.addEventListener('input', (e) => {
            renderResponses(e.target.value);
        });

        // Modal Event Listeners
        saveLabelBtn.addEventListener('click', () => {
            if (newResponseId) {
                const responses = categories[activeCategory].responses;
                const responseIndex = responses.findIndex(r => r.id === newResponseId);
                if (responseIndex > -1) {
                    responses[responseIndex].label = modalLabelInput.value || '';
                    saveToLocalStorage();
                }
                newResponseId = null;
                modalLabelInput.value = '';
                labelModal.classList.add('hidden');
                renderResponses();
            }
        });

        cancelLabelBtn.addEventListener('click', () => {
            if (newResponseId) {
                deleteResponse(newResponseId);
                newResponseId = null;
            }
            modalLabelInput.value = '';
            labelModal.classList.add('hidden');
        });

        deleteConfirmBtn.addEventListener('click', () => {
            if (responseToDeleteId) {
                deleteResponse(responseToDeleteId);
                responseToDeleteId = null;
                deleteModal.classList.add('hidden');
            }
        });

        deleteCancelBtn.addEventListener('click', () => {
            responseToDeleteId = null;
            deleteModal.classList.add('hidden');
        });

        // Initial render
        window.onload = renderContent;
    </script>
</body>
</html>
