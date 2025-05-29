```
pair_mix(g,P::ClapeyronParam,Q::ClapeyronParam)::PairParam
pair_mix(g,P::ClapeyronParam,Q::ClapeyronParam)::PairParam
```

General combining rule for a pair and a single parameter. returns a pair parameter `P` with non diagonal entries equal to:

```
Pᵢⱼ = g(Pᵢ,Pⱼ,Qᵢ,Qⱼ,Qᵢⱼ)
```

Where `f` is a 'combining' function that follows the rules:

```
Pᵢⱼ = Pⱼᵢ = g(Pᵢ,Pⱼ,Qᵢ,Qⱼ,Qᵢⱼ) = g(Pⱼ,Pᵢ,Qⱼ,Qᵢ,Qᵢⱼ)
g(Pᵢ,Pᵢ,Qᵢ,Qᵢ,Qᵢ) = Pᵢ
```

it is a more general form of `kij_mix`, where `kij_mix(f,P,Q) == pair_mix(g,P,Q)` is correct if:

```
f(Pᵢ,Pⱼ,Qᵢⱼ) = g(Pᵢ,Pⱼ,_,_,Qᵢⱼ)

If you pass a `SingleParam` or a vector as input for `Q`, then `Qᵢⱼ` will be considered 0.
```
