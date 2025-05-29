```
Williamson <: Factorization
```

正定行列 `V` のウィリアムソン分解の行列因子化タイプです。これは、対応する行列因子化関数 [`williamson(_)`](@ref) の返り値の型です。

`F::Williamson` が因子化オブジェクトである場合、`S` と `spectrum` は `F.S` と `F.spectrum` を介して取得できます。

分解を反復することで、成分 `S` と `spectrum` が得られます。

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
S因子:
2×2 Matrix{Float64}:
 0.448828  -1.95959
 0.61311   -0.448828
シンプレクティックスペクトル:
1要素のベクトル{Float64}:
 1.7320508075688772

julia> isapprox(F.S * V * F.S', Diagonal(repeat(F.spectrum, 2)))
true

julia> S, spectrum = F; # 反復を介した分解

julia> S == F.S && spectrum == F.spectrum
true
```
