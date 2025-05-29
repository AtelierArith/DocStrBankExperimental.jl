```
deficiency(rn::ReactionSystem)
```

Calculate the deficiency of a reaction network.

Here the deficiency, $\delta$, of a network with $n$ reaction complexes, $\ell$ linkage classes and a rank $s$ stoichiometric matrix is

$$
\delta = n - \ell - s
$$

For example,

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
δ = deficiency(sir)
```
