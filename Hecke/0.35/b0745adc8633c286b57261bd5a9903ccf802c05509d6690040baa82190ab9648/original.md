```
radical_extension(n::Int, a::NumFieldElem, s = "_$";
               check = true, cached = true) -> NumField, NumFieldElem
```

Given an element $a$ of a number field $K$ and an integer $n$, create the simple extension of $K$ with the defining polynomial $x^n - a$.

# Examples

```jldoctest
julia> radical_extension(5, QQ(2), "a")
(Number field of degree 5 over QQ, a)
```
