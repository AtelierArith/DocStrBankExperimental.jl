```
ExternalDocstrings
```

ExternalDocstrings.jl is a helper for writing docstrings in markdown files.

# Usage

Create markdown files in `src/docs/` (where `src/MyPackage.jl` is the main package source file).  Put the following line inside of `MyPackage` namespace:

```julia
ExternalDocstrings.@define_docstrings
```

It defines a docstring for name `MyPackage.$name` using the markdown content in `src/docs/$name.md`.

# Extended help

## Markdown transformations

To use standard markdown (and CommonMark) while supporting special syntaxes for Julia docstring, ExternalDocstrings.jl performs a couple of transformations:

(1) Code fence notation

```julia
    # ...
    ```

is transformed into

    ```jldoctest LABEL
    # ...
    ```

where `LABEL` is a label unique to the markdown file (i.e., all code blocks in one markdown
file are executed in the same session).

(2) To help doctests for non-REPL code block,

    nothing  # hide
    # output

is inserted at the end of code block if it does not look like a REPL session and does not
already have `# output`.

(3) `<kbd>KEY</kbd>` is replaced by `_KEY_`.

## Tips

### Disable doctest

To enable syntax highlighting without doctest, use use slightly different code fence
notations such as

    ```JULIA
    this_is_not_doctested() = nothing
    ```

### Vendoring

ExternalDocstrings.jl written as a single-source package to help vendoring.  For example, it
can be installed simply by:

```

bash wget https://raw.githubusercontent.com/tkf/ExternalDocstrings.jl/main/src/ExternalDocstrings.jl -O src/ExternalDocstrings.jl ```
