```
generaldyne(state::GaussianState, indices::Vector; proj = (ħ/2)I) -> Generaldyne
generaldyne(state::GaussianState, index::Int; proj = (ħ/2)I) -> Generaldyne
```

ガウス状態 `state` のサブシステムを `proj` に基づいて `indices` で示された部分に投影し、`Generaldyne` オブジェクトを返します。キーワード引数 `proj` は以下の形式を取ることができます：

  * `proj` が行列の場合、サブシステムはランダムにサンプリングされた平均と共分散行列 `result` を持つガウス状態に投影されます。
  * `proj` がガウス状態の場合、サブシステムは `proj` に投影されます。

`result` とマッピングされた状態 `output` は、Generaldyne オブジェクト `M` から `M.result` と `M.output` を介して取得できます。分解を繰り返すことで、成分 `result` と `output` が得られます。

測定されたモードは、一般的なダイナミクス測定の後に真空状態に置き換えられることに注意してください。

# 例

```
julia> st = squeezedstate(QuadBlockBasis(3), 1.0, pi/4);

julia> M = generaldyne(st, [1, 3])
Generaldyne{GaussianState{QuadBlockBasis{Int64}, Vector{Float64}, Matrix{Float64}}, GaussianState{QuadBlockBasis{Int64}, Vector{Float64}, Matrix{Float64}}}
result:
GaussianState for 2 modes.
  symplectic basis: QuadBlockBasis
mean: 4-element Vector{Float64}:
  0.26967410461090285
  1.4683993027500133
 -1.84631450059537
  0.16832788926417352
covariance: 4×4 Matrix{Float64}:
 1.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  1.0  0.0
 0.0  0.0  0.0  1.0
output state:
GaussianState for 3 modes.
  symplectic basis: QuadBlockBasis
mean: 6-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
covariance: 6×6 Matrix{Float64}:
 1.0   0.0      0.0  0.0   0.0      0.0
 0.0   1.19762  0.0  0.0  -2.56458  0.0
 0.0   0.0      1.0  0.0   0.0      0.0
 0.0   0.0      0.0  1.0   0.0      0.0
 0.0  -2.56458  0.0  0.0   6.32677  0.0
 0.0   0.0      0.0  0.0   0.0      1.0

julia> result, state = M; # destructuring via iteration

julia> result == M.result && state == M.state
true
```
