```
ein"ij,jk -> ik"(A,B)
```

String macro interface which understands `numpy.einsum`'s notation. Translates strings into `StaticEinCode`-structs that can be called to evaluate an `einsum`. To control evaluation order, use parentheses - instead of an `EinCode`, a `NestedEinsum` is returned which evaluates the expression according to parens. The valid character ranges for index-labels are `a-z` and `α-ω`.

# example

```jldoctest; setup = :(using OMEinsum)
julia> a, b, c = rand(10,10), rand(10,10), rand(10,1);

julia> ein"ij,jk,kl -> il"(a,b,c) ≈ ein"(ij,jk),kl -> il"(a,b,c) ≈ a * b * c
true
```
