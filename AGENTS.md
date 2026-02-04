# AGENTS.md

Guidelines for AI agents and contributors working on this repository.

## Commit Standards

### Semantic Commits

All commits must follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

```
<type>: <description>

[optional body]

[optional footer(s)]
```

**Allowed types:**

| Type | Description |
|------|-------------|
| `feat` | A new feature or functionality |
| `fix` | A bug fix |
| `docs` | Documentation only changes |
| `style` | Code style changes (formatting, whitespace) |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `test` | Adding or updating tests |
| `chore` | Maintenance tasks, dependency updates |
| `ci` | Changes to CI configuration files and scripts |

### Commit Size

- Commits should be **small and reviewable**
- Each commit should represent a single logical change
- Prefer multiple small commits over one large commit
- Each commit should leave the repository in a working state

## Code Quality

### YAML Files

- All YAML files must be valid and properly formatted
- Use 2-space indentation
- Run `actionlint` on `action.yml` before committing
- Validate GitHub Actions workflow syntax

### JavaScript (Inline in action.yml)

Since this action uses `actions/github-script@v8` with inline JavaScript:

- Use modern ES2020+ syntax
- Use `const` and `let`, never `var`
- Use async/await for asynchronous operations
- Add comments for complex logic
- Keep functions focused and single-purpose
- Handle errors gracefully with try/catch

### General Guidelines

- No trailing whitespace
- Files must end with a newline
- Use descriptive variable and function names

## CI Requirements

The following checks must pass before merging:

1. **actionlint** - Validates GitHub Actions workflow and action syntax
2. **YAML validation** - Ensures all YAML files are syntactically correct

## Repository Structure

```
merge-gatekeeper/
├── AGENTS.md           # This file
├── README.md           # Usage documentation
├── action.yml          # The composite action definition
└── .github/
    └── workflows/
        └── ci.yml      # CI validation workflow
```

## Testing Changes

When modifying the action:

1. Ensure `actionlint` passes locally if available
2. Test in a real workflow if possible
3. Verify all inputs work as documented
4. Check that the summary output renders correctly
