```
delay = Delay(T)
```

The Delay struct is meant to add a delay to a sequence by using a sum operator.

# Arguments

  * `T`: (`::Real`, `[s]`) time delay value

# Returns

  * `delay`: (`::Delay`) delay struct

# Examples

```julia-repl
julia> delay = Delay(0.5)

julia> s = Sequence([Grad(1, 1, 0.1)])

julia> seq = delay + s; plot_seq(seq)
```
