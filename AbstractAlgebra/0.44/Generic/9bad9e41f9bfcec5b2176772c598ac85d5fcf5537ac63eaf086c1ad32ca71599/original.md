```
size(Y::YoungTableau)
```

Return `size` of the smallest array containing `Y`, i.e. the tuple of the number of rows and the number of columns of `Y`.

# Examples

```jldoctest
julia> y = YoungTableau([4,3,1]); size(y)
(3, 4)
```
