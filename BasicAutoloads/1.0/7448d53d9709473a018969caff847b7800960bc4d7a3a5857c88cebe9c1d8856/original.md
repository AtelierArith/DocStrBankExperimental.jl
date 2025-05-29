```
register_autoloads(autoloads::Vector{Pair{Vector{String}, Expr}})
register_autoloads([
    [trigger1, trigger2, ...]   => expr1,
    [trigger10, trigger11, ...] => expr2,
    ...
])
```

Register expressions to be executed when a trigger is found in the REPL's input.

Each `trigger` must be a `String`. If the `trigger` is found as a symbol (e.g. variable, function, or macro name) in an input expression to the REPL, the corresponding `expr` is evaluated. Each `expr` must be an `Expr` and is evaluated with `Main.eval(expr)`. Each unique `expr`, up to equality, is evaluated at most once.

This function is meant to be called from `~/.julia/config/startup.jl` (or wherever your startup.jl file happens to be stored), but will also work if called from the REPL.

# Example

```julia
if isinteractive()
    import BasicAutoloads
    BasicAutoloads.register_autoloads([
        ["@b", "@be"]            => :(using Chairmarks),
        ["@benchmark"]           => :(using BenchmarkTools),
        ["@test", "@testset", "@test_broken", "@test_deprecated", "@test_logs",
        "@test_nowarn", "@test_skip", "@test_throws", "@test_warn", "@inferred"] =>
                                    :(using Test),
        ["@about"]               => :(using About; macro about(x) Expr(:call, About.about, x) end),
    ])
end
```
