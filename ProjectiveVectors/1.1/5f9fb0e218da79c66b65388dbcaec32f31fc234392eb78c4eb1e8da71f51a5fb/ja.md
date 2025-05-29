```
isreal(v::PVector{T}, tol::Real)
```

ベクトル `v` の完全に実数の代表が存在するかどうかを確認します。このために、まず `v` は正規化され、次に各成分の最大エントリが実数にされます。この後、すべての座標の虚部が `tol` より小さい場合、そのベクトルは実数と見なされます。

## 例

```julia
julia> a, b = rand(ComplexF64, 2);
julia> v = PVector(a .* [1,2,3]) × PVector(b .* [4, 5]);
julia> isreal(v, 1e-6)
true
```
