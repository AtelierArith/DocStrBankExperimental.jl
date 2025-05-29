An [`Abbreviation`](@ref) for including the function name matching the method of the docstring.

# Usage

This is mostly useful for not repeating the function name in docstrings where the user wants to retain full control of the argument list, or the latter does not exist (eg generic functions).

Note that the generated docstring snippet is not quoted, use indentation or explicit quoting.

# Example

```julia
"""
    $(FUNCTIONNAME)(d, θ)

Calculate the logdensity `d` at `θ`.

Users should define their own methods for `FUNCTIONNAME`.
"""
function logdensity end
```
