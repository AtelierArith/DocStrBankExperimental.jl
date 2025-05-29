```
Machines(S::Array{Rational{Int}, 1})
```

Generates a set of machines with speeds determined by the `S` array, denoted by `Q_1`, `Q_2`, etc.

# Example

```julia-repl
julia> Machines([1, 1//2, 2])
A set of 3 machine(s):
    Machine Q_1
    Machine Q_2:     [s = 1//2]
    Machine Q_3:     [s = 2]

```
