```
setdefaults!(rn, newdefs)
```

Sets the default (initial) values of parameters and species in the `ReactionSystem`, `rn`.

For example,

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
setdefaults!(sir, [:S => 999.0, :I => 1.0, :R => 1.0, :β => 1e-4, :ν => .01])

# or
@parameter β ν
@variables t
@species S(t) I(t) R(t)
setdefaults!(sir, [S => 999.0, I => 1.0, R => 0.0, β => 1e-4, ν => .01])
```

gives initial/default values to each of `S`, `I` and `β`

Notes:

  * Can not be used to set default values for species, variables or parameters of subsystems or constraint systems. Either set defaults for those systems directly, or [`flatten`](@ref) to collate them into one system before setting defaults.
  * Defaults can be specified in any iterable container of symbols to value pairs or symbolics to value pairs.
