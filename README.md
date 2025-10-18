# projinit

A CLI tool to quickly bootstrap new projects with templates.

## Installation

Make the script executable:

```bash
chmod +x projinit
```

Add to PATH (optional):

```bash
# Add this line to ~/.bashrc or ~/.zshrc
export PATH="$PATH:/home/oskari/Desktop/pyt/projinit"
```

Then reload:
```bash
source ~/.bashrc  # or source ~/.zshrc
```

## Usage

```bash
projinit <type> <name> [options]
```

### Project Types

- **express** - Node.js Express web server
- **expo** - React Native mobile app with Expo
- **github** - Create empty remote GitHub repository

## Examples

### Express Projects

```bash
# Basic JavaScript project
projinit express my-api

# TypeScript project
projinit express my-api --ts

# With extra libraries
projinit express my-api --with cors helmet morgan

# With GitHub repository
projinit express my-api --ts --github

# Create and push existing code
projinit express my-api --create-repo
```

### Expo Projects

```bash
# Basic Expo project
projinit expo my-app

# With NativeWind (Tailwind CSS for React Native)
projinit expo my-app --nativewind

# With extra libraries
projinit expo my-app --with axios @react-navigation/native
```

### GitHub Repository

```bash
# Create empty public repository
projinit github my-repo

# Create private repository
projinit github my-repo --private

# Create and push current directory
projinit github my-repo --push-current

# With description
projinit github my-repo --description "My awesome project"
```

## Available Flags

### Global Flags
- `--with <libs...>` - Install additional libraries
- `--github` - Create GitHub repository (for express/expo)
- `--private` - Make GitHub repository private
- `--description <text>` - GitHub repository description
- `--create-repo` - Create repo and push new project

### Express Flags
- `--ts, --typescript` - Use TypeScript instead of JavaScript

### Expo Flags
- `--nativewind` - Setup project with NativeWind

### GitHub Flags
- `--push-current` - Push current directory to repository

## Requirements

- Node.js & npm (for express/expo projects)
- GitHub CLI (`gh`) for GitHub features
  - Install: `sudo apt install gh`
  - Login: `gh auth login`
- Git (for version control)

## Project Structure

```
express-project/
├── src/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── middlewares/
│   ├── utils/
│   └── index.js (or .ts)
├── config/
├── .env
├── .gitignore
├── package.json
└── README.md
```

## Default Libraries

### Express
- cors, helmet, morgan, dotenv, nodemon, mongoose, bcrypt, jsonwebtoken

### Expo
- expo-constants, expo-font, axios

Override defaults with `--with`:
```bash
projinit express api --with express cors  # Only install cors
```

## Tips

- Use `--ts` for new Express projects to get TypeScript setup
- Use `--github` to automatically create and push to GitHub
- Use `--private` for private repositories
- Use `--push-current` to push existing local code to GitHub

## License

MIT