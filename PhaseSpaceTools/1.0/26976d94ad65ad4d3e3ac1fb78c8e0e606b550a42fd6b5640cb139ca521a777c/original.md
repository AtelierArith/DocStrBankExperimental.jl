```
a = randnc(N...)
```

Return an array of dimension `length(N)`, containing samples of complex random variables with mean zero and variance one:

$$
⟨|a|^2⟩ = 1; ⟨a^2⟩ = ⟨(a^*) ^2⟩ = 0,
$$

Useful for creating a range of noises that show up in phase-space simulations.

Usage:

`a = randnc(10)` returns a `10-element Array{Complex{Float64},1}`.

`a = randnc(50,100)` returns a `50x100-element Array{Complex{Float64},2}`.
