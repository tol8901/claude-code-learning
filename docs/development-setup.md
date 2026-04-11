# Pomodorro Timer Development Environment Setup Guide

## 1. Prerequisites

### 1.1 System Requirements
- **Operating System**: Windows 10+, macOS 10.15+, or Linux (Ubuntu 20.04+)
- **Node.js**: Version 18.x or 20.x (LTS recommended)
- **npm**: Version 9.x or higher (comes with Node.js)
- **Git**: Version 2.30+ for version control
- **Code Editor**: VS Code (recommended) or any modern IDE

### 1.2 Required Software
```bash
# Verify installations
node --version          # Should show v18.x or v20.x
npm --version           # Should show 9.x or higher
git --version           # Should show 2.30+
code --version          # If using VS Code
```

### 1.3 Browser Requirements (for development)
- **Chrome**: Latest version (for development and testing)
- **Firefox**: Latest version (for cross-browser testing)
- **Safari**: Latest version (for macOS testing)
- **Edge**: Latest version (optional)

## 2. Project Setup

### 2.1 Clone Repository
```bash
# Clone the repository
git clone https://github.com/your-username/pomodorro-timer.git
cd pomodorro-timer

# Or if using SSH
git clone git@github.com:your-username/pomodorro-timer.git
cd pomodorro-timer
```

### 2.2 Install Dependencies
```bash
# Install project dependencies
npm ci

# Alternative: clean install
rm -rf node_modules package-lock.json
npm install
```

### 2.3 Environment Configuration
```bash
# Copy environment template
cp .env.example .env.local

# Edit environment variables
# .env.local
VITE_APP_ENV=development
VITE_APP_VERSION=1.0.0-dev
VITE_API_BASE_URL=http://localhost:3000
VITE_SENTRY_DSN=              # Leave empty for development
VITE_ANALYTICS_ID=            # Leave empty for development
```

## 3. Development Tools Setup

### 3.1 VS Code Configuration
Install recommended extensions:
```json
// .vscode/extensions.json
{
  "recommendations": [
    "dbaeumer.vscode-eslint",
    "esbenp.prettier-vscode",
    "bradlc.vscode-tailwindcss",
    "ms-vscode.vscode-typescript-next",
    "christian-kohler.npm-intellisense",
    "wix.vscode-import-cost",
    "ms-playwright.playwright",
    "firsttris.vscode-jest-runner"
  ]
}
```

### 3.2 Browser Extensions (Recommended)
- **React Developer Tools**: For React component inspection
- **Redux DevTools**: For state management debugging
- **Lighthouse**: For performance auditing
- **axe DevTools**: For accessibility testing
- **JSON Formatter**: For API response inspection

### 3.3 Git Configuration
```bash
# Set up Git hooks
npm run prepare  # Sets up Husky hooks

# Configure Git (if not already done)
git config --local user.name "Your Name"
git config --local user.email "your.email@example.com"
```

## 4. Development Workflow

### 4.1 Starting Development Server
```bash
# Start development server with hot reload
npm run dev

# Server will start at http://localhost:5173
# Open browser to http://localhost:5173
```

### 4.2 Available Scripts
```bash
# Development
npm run dev              # Start development server
npm run dev:host         # Start with network access
npm run dev:https        # Start with HTTPS

# Building
npm run build            # Build for production
npm run build:staging    # Build for staging
npm run build:analyze    # Analyze bundle size

# Testing
npm run test             # Run all tests
npm run test:unit        # Run unit tests only
npm run test:integration # Run integration tests
npm run test:e2e         # Run E2E tests
npm run test:watch       # Run tests in watch mode
npm run test:coverage    # Generate test coverage report

# Code Quality
npm run lint             # Run ESLint
npm run lint:fix         # Fix linting issues
npm run type-check       # TypeScript type checking
npm run format           # Format code with Prettier
npm run format:check     # Check formatting without fixing

# Utilities
npm run prepare          # Set up Git hooks
npm run clean            # Clean build artifacts
npm run storybook        # Start Storybook (if configured)
```

### 4.3 Development Commands Cheat Sheet
```bash
# Common development workflow
git checkout -b feature/your-feature  # Create feature branch
npm run dev                           # Start development
# Make changes...
npm run lint                          # Check code quality
npm run test                          # Run tests
npm run build                         # Verify build works
git add .                             # Stage changes
git commit -m "feat: your feature"    # Commit changes
git push origin feature/your-feature  # Push to remote
```

## 5. Project Structure

### 5.1 Directory Layout
```
pomodorro-timer/
├── src/                    # Source code
│   ├── components/         # React components
│   │   ├── common/         # Shared components
│   │   ├── timer/          # Timer-related components
│   │   ├── settings/       # Settings components
│   │   └── history/        # History components
│   ├── hooks/              # Custom React hooks
│   ├── contexts/           # React contexts
│   ├── utils/              # Utility functions
│   ├── types/              # TypeScript type definitions
│   ├── styles/             # Global styles
│   ├── assets/             # Static assets (images, fonts)
│   └── __tests__/          # Test files
├── public/                 # Public assets
├── cypress/                # E2E tests
├── docs/                   # Documentation
├── scripts/                # Build and utility scripts
├── .github/                # GitHub workflows
└── config/                 # Build configuration
```

### 5.2 Key Configuration Files
```
├── package.json           # Dependencies and scripts
├── tsconfig.json         # TypeScript configuration
├── vite.config.ts        # Vite build configuration
├── tailwind.config.js    # Tailwind CSS configuration
├── eslint.config.js      # ESLint configuration
├── prettier.config.js    # Prettier configuration
├── jest.config.js        # Jest test configuration
├── cypress.config.ts     # Cypress configuration
└── .env.example          # Environment variables template
```

## 6. Development Practices

### 6.1 Code Style Guidelines
- **Indentation**: 2 spaces (no tabs)
- **Quotes**: Single quotes for JavaScript, double for JSX
- **Semicolons**: Always use semicolons
- **Line length**: Maximum 100 characters
- **Import order**: Built-in → external → internal → relative

### 6.2 Git Workflow
```bash
# Feature branch workflow
git checkout main
git pull origin main
git checkout -b feature/feature-name

# Make changes and commit
git add .
git commit -m "feat: add feature description"

# Keep branch updated
git fetch origin
git rebase origin/main

# Push changes
git push origin feature/feature-name

# Create pull request on GitHub
```

### 6.3 Commit Message Convention
```
type(scope): description

Types:
- feat: New feature
- fix: Bug fix
- docs: Documentation changes
- style: Code style changes (formatting, etc.)
- refactor: Code refactoring
- test: Adding or updating tests
- chore: Maintenance tasks

Examples:
feat(timer): add pause/resume functionality
fix(settings): correct validation for work duration
docs(readme): update installation instructions
```

## 7. Testing Setup

### 7.1 Running Tests
```bash
# Run all tests
npm test

# Run specific test file
npm test -- src/components/TimerDisplay.test.tsx

# Run tests with coverage
npm run test:coverage

# Open coverage report
open coverage/lcov-report/index.html

# Run E2E tests
npm run test:e2e

# Run E2E tests in headed mode
npm run test:e2e:headed
```

### 7.2 Test File Structure
```typescript
// Example test file structure
import { render, screen, fireEvent } from '@testing-library/react';
import { TimerDisplay } from './TimerDisplay';

describe('TimerDisplay', () => {
  it('renders timer with correct format', () => {
    render(<TimerDisplay timeRemaining={1500} />);
    expect(screen.getByText('25:00')).toBeInTheDocument();
  });

  it('handles user interactions', () => {
    const onStart = jest.fn();
    render(<TimerDisplay timeRemaining={1500} onStart={onStart} />);
    
    fireEvent.click(screen.getByText('Start'));
    expect(onStart).toHaveBeenCalledTimes(1);
  });
});
```

### 7.3 Debugging Tests
```bash
# Debug Jest tests
npm run test:debug

# Debug specific test
npm run test:debug -- --testNamePattern="TimerDisplay"

# Run tests with verbose output
npm test -- --verbose

# Update snapshots
npm test -- --updateSnapshot
```

## 8. Debugging

### 8.1 Browser DevTools
- **React DevTools**: Inspect component hierarchy and props
- **Redux DevTools**: Debug state management
- **Network Tab**: Monitor API requests and responses
- **Console**: JavaScript errors and logs
- **Sources**: Debug TypeScript source maps
- **Performance**: Profile application performance

### 8.2 VS Code Debugging
```json
// .vscode/launch.json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "chrome",
      "request": "launch",
      "name": "Launch Chrome",
      "url": "http://localhost:5173",
      "webRoot": "${workspaceFolder}/src",
      "sourceMapPathOverrides": {
        "webpack:///src/*": "${webRoot}/*"
      }
    },
    {
      "type": "node",
      "request": "launch",
      "name": "Debug Jest Tests",
      "program": "${workspaceFolder}/node_modules/.bin/jest",
      "args": ["--runInBand", "--no-coverage"],
      "console": "integratedTerminal",
      "internalConsoleOptions": "neverOpen"
    }
  ]
}
```

### 8.3 Common Debugging Commands
```bash
# Check for TypeScript errors
npm run type-check

# Check for linting errors
npm run lint

# Check bundle size
npm run build:analyze

# Check performance
npm run lighthouse

# Check accessibility
npm run a11y
```

## 9. Performance Optimization

### 9.1 Development Performance Tips
```typescript
// Use React.memo for expensive components
const ExpensiveComponent = React.memo(({ data }) => {
  // Component implementation
});

// Use useMemo for expensive calculations
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);

// Use useCallback for stable function references
const handleClick = useCallback(() => {
  // Event handler
}, [dependencies]);

// Lazy load components
const Settings = React.lazy(() => import('./Settings'));
```

### 9.2 Performance Monitoring
```bash
# Build with performance analysis
npm run build:analyze

# Run Lighthouse audit
npm run lighthouse

# Check bundle size
npx webpack-bundle-analyzer dist/stats.json

# Monitor memory usage
# Use Chrome DevTools Memory tab
```

## 10. Troubleshooting

### 10.1 Common Issues

#### Issue: Dependencies won't install
```bash
# Clear npm cache
npm cache clean --force

# Delete node_modules and lock files
rm -rf node_modules package-lock.json

# Reinstall
npm install
```

#### Issue: TypeScript errors
```bash
# Check TypeScript configuration
npx tsc --noEmit

# Check for missing types
npm install @types/package-name --save-dev
```

#### Issue: ESLint/Prettier conflicts
```bash
# Fix all auto-fixable issues
npm run lint:fix

# Format all files
npm run format

# Check configuration
npx eslint --print-config src/App.tsx
```

#### Issue: Tests failing
```bash
# Run tests with more detail
npm test -- --verbose

# Update snapshots if UI changed
npm test -- --updateSnapshot

# Run specific failing test
npm test -- --testNamePattern="TestName"
```

#### Issue: Development server not starting
```bash
# Check if port is in use
lsof -i :5173

# Kill process on port
kill -9 $(lsof -t -i:5173)

# Start with different port
npm run dev -- --port=3000
```

### 10.2 Getting Help
- **Check documentation**: Review this guide and other docs
- **Search issues**: Check GitHub issues for similar problems
- **Debug logs**: Run with `--verbose` flag for more details
- **Ask for help**: Create a GitHub issue with detailed description

## 11. Advanced Setup

### 11.1 Docker Development
```dockerfile
# Dockerfile.dev
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .

EXPOSE 5173

CMD ["npm", "run", "dev"]
```

```bash
# Build and run with Docker
docker build -f Dockerfile.dev -t pomodorro-dev .
docker run -p 5173:5173 -v $(pwd):/app pomodorro-dev
```

### 11.2 Remote Development
```bash
# Develop on remote server
ssh user@server
git clone <repository>
cd pomodorro-timer
npm install
npm run dev -- --host 0.0.0.0

# Access from local machine
# http://server-ip:5173
```

### 11.3 Multiple Environment Setup
```bash
# Set up different environments
cp .env.example .env.development
cp .env.example .env.staging
cp .env.example .env.production

# Run with specific environment
NODE_ENV=development npm run dev
NODE_ENV=staging npm run build
```

## 12. Productivity Tips

### 12.1 VS Code Shortcuts
- **Format Document**: Shift + Alt + F (Windows) / Shift + Option + F (Mac)
- **Quick Fix**: Ctrl + . (Windows) / Cmd + . (Mac)
- **Go to Definition**: F12
- **Find All References**: Shift + F12
- **Rename Symbol**: F2
- **Toggle Terminal**: Ctrl + ` (Windows) / Cmd + ` (Mac)

### 12.2 Useful Commands
```bash
# See available scripts
npm run

# Check for outdated packages
npm outdated

# Update packages
npm update

# Clean install
npm ci

# Run security audit
npm audit
```

### 12.3 Development Tools
- **React Developer Tools**: Browser extension for React debugging
- **Redux DevTools**: For state management debugging
- **Lighthouse CI**: For performance monitoring
- **Husky**: For Git hooks
- **lint-staged**: For pre-commit linting

## 13. Maintenance

### 13.1 Regular Tasks
```bash
# Weekly maintenance
npm update              # Update dependencies
npm audit fix           # Fix security vulnerabilities
npm run lint:fix        # Fix linting issues
npm run format          # Format code
npm test                # Run tests

# Monthly maintenance
npm audit               # Security audit
npm run build:analyze   # Analyze bundle size
npm run lighthouse      # Performance audit
```

### 13.2 Keeping Dependencies Updated
```bash
# Check for updates
npx npm-check-updates

# Update all dependencies
npx npm-check-updates -u
npm install

# Update specific dependency
npm install package-name@latest
```

## 14. Next Steps

### 14.1 After Setup
1. Verify installation by running `npm run dev`
2. Open http://localhost:5173 in your browser
3. Run tests with `npm test`
4. Check code quality with `npm run lint`
5. Start developing your first feature

### 14.2 Learning Resources
- **React Documentation**: https://react.dev
- **TypeScript Handbook**: https://www.typescriptlang.org/docs
- **Vite Guide**: https://vitejs.dev/guide
- **Testing Library**: https://testing-library.com/docs/react-testing-library/intro
- **Tailwind CSS**: https://tailwindcss.com/docs

### 14.3 Getting Help
- **Documentation**: Check the `/docs` directory
- **GitHub Issues**: Report bugs or request features
- **Code Review**: Submit pull requests for review
- **Team Communication**: Use team channels for questions

## 15. Appendix

### 15.1 Environment Variables Reference
```bash
# Required variables
VITE_APP_ENV=development|staging|production
VITE_APP_VERSION=1.0.0

# Optional variables
VITE_API_BASE_URL=http://localhost:3000
VITE_SENTRY_DSN=your-sentry-dsn
VITE_ANALYTICS_ID=your-analytics-id
VITE_FEATURE_FLAGS=enabled-features
```

### 15.2 Common Errors and Solutions
| Error | Solution |
|-------|----------|
| `Cannot find module` | Run `npm install` |
| `Port already in use` | Change port or kill process |
| `TypeScript compilation failed` | Check types and run `npm run type-check` |
| `ESLint errors` | Run `npm run lint:fix` |
| `Test failures` | Check test output and update snapshots |

### 15.3 Useful Aliases
```bash
# Add to your shell profile (.bashrc, .zshrc)
alias pdev='npm run dev'
alias ptest='npm test'
alias plint='npm run lint'
alias pbuild='npm run build'
alias pformat='npm run format'
alias pcoverage='npm run test:coverage'
```

This guide should help you get started with the Pomodorro Timer development environment. If you encounter any issues not covered here, please check the GitHub issues or contact the development team.