```
qr(A::StaticMatrix,
   pivot::Union{Val{true}, Val{false}, LinearAlgebra.PivotingStrategy} = Val(false))
```

Compute the QR factorization of `A`. The factors can be obtained by iteration:

```jldoctest qr
julia> A = @SMatrix rand(3,4);

julia> Q, R = qr(A);

julia> Q * R ≈ A
true
```

or by using `getfield`:

```jldoctest qr
julia> F = qr(A);

julia> F.Q * F.R ≈ A
true
```
