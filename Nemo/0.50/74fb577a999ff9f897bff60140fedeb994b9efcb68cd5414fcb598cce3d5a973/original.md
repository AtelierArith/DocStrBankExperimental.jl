```
number_field(f::QQPolyRingElem, s::VarName;
            cached::Bool = true, check::Bool = true)
```

Return a tuple $R, x$ consisting of the parent object $R$ and generator $x$ of the number field $\mathbb{Q}[x]/(f)$ where $f$ is the supplied polynomial. The supplied string `s` specifies how the generator of the number field should be printed. If `s` is not specified, it defaults to `_a`.

# Examples

```jldoctest
julia> R, x = polynomial_ring(QQ, "x");

julia> K, a = number_field(x^3 + 3x + 1, "a")
(Number field of degree 3 over QQ, a)

julia> K
Number field with defining polynomial x^3 + 3*x + 1
  over rational field
```
