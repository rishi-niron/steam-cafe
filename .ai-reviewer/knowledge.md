# steam-cafe reviewer notes

## Architecture
This codebase is a React application bootstrapped with Vite and TypeScript. The structure is organized around a main `App` component that manages routing for multiple pages, each represented as a separate React component stored in the `src/pages` directory. The use of the `pages.ts` file helps in centralizing route definitions and associated components.

## Conventions
- **File Structure**: Pages are organized as individual files named sequentially (e.g., `Page1.tsx`, `Page2.tsx`, …, `Page40.tsx`) located in the `src/pages` directory. This systematic naming allows for easy navigation and auto-imports.
- **Component Naming**: Each page component is exported by default and named according to its functionality (e.g., `Page1`, `Page2`). This reflects a clear and consistent naming pattern that enhances readability.
- **Routing**: Routing is managed using `react-router-dom`, and pages are rendered within the `<Routes>` component in `src/App.tsx`. 
- **CSS and Styling**: The application uses `.css` files for styles, indicated by the import statements in `App.tsx` and `main.tsx`. Consistency in class naming and styles should be maintained.
- **TypeScript Configuration**: The presence of `tsconfig.json` with references to app and node configuration files suggests a monorepo or multi-project setup, which impacts how TypeScript features are utilized across the application.

## Intentional non-standard choices
- The exclusion of `react` compiler in Vite (`README.md`) intentionally enhances development and build performance. This design decision could deviate from typical setups where such features may be enabled for added safety and optimization in type checking.
- Use of `oxlint` as a primary linter instead of more common choices like ESLint; this approach is specified in the `README.md` and aims for specific linting rules relevant to the React and TypeScript setup.

## Watch out for
- **Unused Imports**: Components such as `Page1.tsx`, `Page2.tsx`, etc., currently contain only an `<h1>` tag without any business logic. If similar patterns continue, ensure to verify for unused imports and consistent code hygiene.
- **Performance Considerations**: Ensure that large asset files (like images in `App.tsx`) are optimized for size and loading performance, especially when managing multiple routes. Regular audits for unused assets might be required.
- **Route Management**: The use of a central configuration for routes in `pages.ts` is effective, but the large number of pages could lead to issues if not managed correctly. Ensure that all imports are valid and consider lazy loading for potentially heavy components.
- **Handling State**: In components using hooks (e.g., `useState` in `Home`), make sure state updates are correctly managed, especially as the application scales. This prevents potential re-renders that could hamper performance.