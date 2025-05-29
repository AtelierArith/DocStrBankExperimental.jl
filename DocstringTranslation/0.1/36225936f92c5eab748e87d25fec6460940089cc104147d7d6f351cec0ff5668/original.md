```
@switchlang!(lang)
```

Switch the target language for docstring translation and modify the documentation system to automatically translate docstrings.

# Arguments

  * `lang`: The target language code (e.g., "ja", "en") to translate docstrings into.

# Details

This macro performs the following operations:

1. Sets the target language for translation
2. Overrides `Docs.parsedoc` to insert translation engine for individual docstrings
3. Overrides `Documenter.Page` constructor to enable translation of entire documentation pages

# Example

```julia
@switchlang! "ja"  # Switch to Japanese translation
```
