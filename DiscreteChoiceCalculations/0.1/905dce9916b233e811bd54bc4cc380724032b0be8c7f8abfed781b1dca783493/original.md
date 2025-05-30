```julia
ECV_and_probabilities(noise, V)

```

For IID random variables $εᵢ ∼ 	ex{noise}$, return

1. the *expected continuation value (ECV)* `ECV = E[maxᵢ (Vᵢ + εᵢ)]``, and
2. the probabilities of $πᵢ$ of $X = Vᵢ + εᵢ$

as a `NamedTuple{(:ECV,:π)}`, where `π` has the same “shape” as `V`, and other characteristics are retained to the extent possible (eg `SArray`s, `Tuple`s etc are mapped to similar types).
