```
@cast <function definition>
@cast <module definition>
```

Denote a Julia expression is a command. If the expression is a function definition, it will be parsed as a leaf command, if the expression is a module definition or module name, it will be parsed as a node command. This macro must be used with [`@main`](@ref) to create a multi-command CLI.

# Quick Example

```julia
# in a script or module

"""
sum two numbers.

# Args

- `x`: first number
- `y`: second number

# Options

- `-p, --precision=<type>`: precision of the calculation.

# Flags

- `-f, --fastmath`: enable fastmath.

"""
@cast function sum(x, y; precision::String="float32", fastmath::Bool=false)
    # implementation
    return
end

"product two numbers"
@cast function prod(x, y)
    return
end

@main
```
