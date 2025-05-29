```
williamson(form::SymplecticForm, V::AbstractMatrix) -> Williamson
williamson(::Symplectic, form::SymplecticForm, V::AbstractMatrix) -> Williamson
```

正定行列 `V` のウィリアムソン分解を計算し、`Williamson` オブジェクトを返します。

シンプレクティック行列 `S` とシンプレクティックスペクトル `spectrum` は `F.S` と `F.spectrum` を介して取得できます。

分解を繰り返すことで、コンポーネント `S` と `spectrum` が得られます。

# 例

```
julia> V = [7. 2.; 2. 1.]
2×2 Matrix{Float64}:
 7.0  2.0
 2.0  1.0

julia> isposdef(V)
true

julia> F = williamson(BlockForm(1), V)
Williamson{Float64, Matrix{Float64}, Vector{Float64}}
S factor:
2×2 Matrix{Float64}:
 0.448828  -1.95959
 0.61311   -0.448828
シンプレクティックスペクトル:
1-element Vector{Float64}:
 1.7320508075688772

julia> isapprox(F.S * V * F.S', Diagonal(repeat(F.spectrum, 2)))
true

julia> S, spectrum = F; # 繰り返しによる分解

julia> S == F.S && spectrum == F.spectrum
true
```
