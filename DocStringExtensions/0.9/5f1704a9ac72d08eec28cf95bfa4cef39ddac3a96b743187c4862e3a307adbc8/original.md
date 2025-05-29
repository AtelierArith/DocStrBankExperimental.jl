*Extensions for the Julia docsystem.*

# Introduction

This package provides a collection of useful extensions for Julia's built-in docsystem. These are features that are still regarded as "experimental" and not yet mature enough to be considered for inclusion in `Base`, or that have sufficiently niche use cases that including them with the default Julia installation is not seen as valuable enough at this time.

Currently `DocStringExtensions.jl` exports a collection of so-called "abbreviations", which can be used to add useful automatically generated information to docstrings. These include information such as:

  * simplified method signatures;
  * documentation for the individual fields of composite types;
  * import and export lists for modules;
  * and source-linked lists of methods applicable to a particular docstring.

Users are most welcome to suggest additional abbreviation ideas, or implement and submit them themselves. Julia's strong support for program introspection makes this a reasonably straight forward process.

Details of the currently available abbreviations can be viewed in their individual docstrings listed below in the "Exports" section.

# Examples

In simple terms an abbreviation can be used by simply interpolating it into a suitable docstring. For example:

```julia
using DocStringExtensions

"""
A short summary of `func`...

$(SIGNATURES)

where `x` and `y` should both be positive.

# Details

Some details about `func`...
"""
func(x, y) = x + y
```

`$(SIGNATURES)` will be replaced in the above docstring with

````markdown
# Signatures

```julia
func(x, y)
```
````

The resulting generated content can be viewed via Julia's `?` mode or, if `Documenter.jl` is set up, the generated external documentation.

The advantage of using [`SIGNATURES`](@ref) (and other abbreviations) is that docstrings are less likely to become out-of-sync with the surrounding code. Note though that references to the argument names `x` and `y` that have been manually embedded within the docstring are, of course, not updated automatically.

# Exports

  * [`DOCSTRING`](@ref)
  * [`EXPORTS`](@ref)
  * [`FIELDS`](@ref)
  * [`FUNCTIONNAME`](@ref)
  * [`IMPORTS`](@ref)
  * [`LICENSE`](@ref)
  * [`METHODLIST`](@ref)
  * [`README`](@ref)
  * [`SIGNATURES`](@ref)
  * [`TYPEDEF`](@ref)
  * [`TYPEDFIELDS`](@ref)
  * [`TYPEDSIGNATURES`](@ref)
  * [`@template`](@ref)

# Imports

  * `Base`
  * `Core`
