A type to represent the restriction of a function to a direction. Given f : R → Rⁿ, x ∈ Rⁿ and a nonzero direction d ∈ Rⁿ,

```
ϕ = LineModel(nlp, x, d)
```

represents the function ϕ : R → R defined by

```
ϕ(t) := f(x + td).
```
