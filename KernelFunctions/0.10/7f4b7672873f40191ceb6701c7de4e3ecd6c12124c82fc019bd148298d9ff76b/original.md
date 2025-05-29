```
LinearTransform(A::AbstractMatrix)
```

Linear transformation of the input realised by the matrix `A`.

The second dimension of `A` must match the number of features of the target.

# Examples

```jldoctest
julia> A = rand(10, 5); t = LinearTransform(A); X = rand(5, 100);

julia> map(t, ColVecs(X)) == ColVecs(A * X)
true
```
