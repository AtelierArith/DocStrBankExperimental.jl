```
UBCM_reduced_iter!(θ, K, F, x, G)
```

UBCMモデルの次の不動点反復を指数形式を使用して計算し、凸性を維持します。この関数は、速度のために事前に割り当てられたベクトル（`G`と`x`）を更新します。

# 引数

  * `θ`: モデルの最尤パラメータ
  * `K`: 簡約された次数列
  * `F`: 次数列における各次数の頻度
  * `x`: モデルの指数化された最尤パラメータ ( xᵢ = exp(-θᵢ) ) （事前に割り当て済み）
  * `G`: UBCMモデルの次の不動点反復（事前に割り当て済み）

# 例

```jldoctest
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> G = zeros(eltype(model.θᵣ), length(model.θᵣ));

julia> x = zeros(eltype(model.θᵣ), length(model.θᵣ));

julia> UBCM_FP! = θ -> UBCM_reduced_iter!(θ, model.dᵣ, model.f, x, G);

julia> UBCM_FP!(initial_guess(model));

```
