```
qr(A::StaticMatrix,
   pivot::Union{Val{true}, Val{false}, LinearAlgebra.PivotingStrategy} = Val(false))
```

行列 `A` の QR 分解を計算します。因子は反復によって取得できます：

```jldoctest qr
julia> A = @SMatrix rand(3,4);

julia> Q, R = qr(A);

julia> Q * R ≈ A
true
```

または `getfield` を使用して：

```jldoctest qr
julia> F = qr(A);

julia> F.Q * F.R ≈ A
true
```
