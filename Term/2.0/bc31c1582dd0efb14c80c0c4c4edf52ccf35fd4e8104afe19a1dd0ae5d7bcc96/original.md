```
Term.jl
```

Welcome to Term.jl! Term.jl is a Julia library for producing styled, beautiful terminal output.

# Documentation

See https://fedeclaudi.github.io/Term.jl for documentation.

# Demonstration

```julia
using Term
const term_demo = joinpath(dirname(pathof(Term)), "..", "README.jl")
include(term_demo) # view demo
less(term_demo) # see demo code
```

# Example

```julia

```

julia begin     println(@green "this is green")     println(@blue "and this is blue")     println()     println(@bold "this is bold")     println(@underline "and this is underlined") end ```
