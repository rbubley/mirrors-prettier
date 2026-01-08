prettier mirror
===============

This is a fork of the (now archived) https://github.com/pre-commit/mirrors-prettier with the only differences 
being that it is does not autoupdate when new versions of `prettier` are released 
and only references release versions of prettier, not e.g. alpha/beta versions.
It's purpose is to have a stable, reliable source to provide our linting hooks that is able to support
the prettier-plugin-toml for toml support (the archived pre-commit repo does not suppor this).

Mirror of prettier package for pre-commit.

For pre-commit: see https://github.com/pre-commit/pre-commit

For prettier: see https://github.com/prettier/prettier


### Using prettier with pre-commit

Add this to your `.pre-commit-config.yaml`:

```yaml
-   repo: https://github.com/rbubley/mirrors-prettier
    rev: ''  # Use the sha / tag you want to point at
    hooks:
    -   id: prettier
```

*note*: only prettier versions >= 2.1.0 are supported

When using plugins with `prettier` you'll need to declare them under
`additional_dependencies`. For example:

```yaml
-   repo: https://github.com/rbubley/mirrors-prettier
    rev: ''  # Use the sha / tag you want to point at
    hooks:
    -   id: prettier
        additional_dependencies:
        -   prettier@2.1.2
        -   '@prettier/plugin-xml@0.12.0'
```

By default, all files are passed to `prettier`, if you want to limit the
file list, adjust `types` / `types_or` / `files`:

```yaml
    -   id: prettier
        types_or: [css, javascript]
```
