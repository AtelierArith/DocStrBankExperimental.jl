```
compute_lipschitzconstant_boundary(
    gh::Array{Float64,1},
    coords::Array{Array{Float64,1},1},
    boundaryNodes::Set{Int64};
    qdim::Int64 = 1,
    pnorm::Real = 2
)
```

メッシュの境界におけるFEM係数ベクトルとして与えられた関数gのリプシッツ定数を返します。

# 必須引数

  * `gh::Array{Float64,1}`: メッシュ上で離散的に評価された関数。
  * `coords::Array{Array{Float64,1},1}`: ghが評価されたノードの座標の配列。特にboundaryNodesの座標を含みます。
  * `boundaryNodes::Set{Int64}`: 評価される境界に属するノード、すなわちcoordsのエントリのセット。したがって、ghのエントリも選択されます。qdimによって潜在的にシフトされる可能性があります。

# キーワード引数

  * `qdim::Int64 = 1`: 関数ghの成分の数。
  * `pnorm::Real = 2`: 内部距離を測定するために使用されるp-ノルムのパラメータ。
