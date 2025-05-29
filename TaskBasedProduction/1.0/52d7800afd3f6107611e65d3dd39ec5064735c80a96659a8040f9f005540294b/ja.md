```
unitInputDemand(xT::AbstractArray{<:Real}, θ::Real, κ::Real, z::Real, αVec::AbstractArray{<:Real}, skipParamChecks::Bool = false) -> AbstractArray{<:Real}
```

ブループリントスケール `θ`、ブループリント形状 `κ`、生産性 `z`、比較優位値の配列 `αVec`（各労働者タイプごとに1つのH要素を持つ）、およびタスク空間のH-1の閾値の配列 `xT` に基づいて、単位労働需要を計算します。

# 引数

  * `xT`: タスク空間のH-1の閾値の配列。
  * `q`: 生産量
  * `θ`: ブループリントスケールパラメータ。
  * `κ`: ブループリント形状パラメータ。
  * `z`: 生産性パラメータ。
  * `αVec`: H要素を持つ比較優位値の配列。
  * `skipParamChecks`: パラメータチェックをスキップするかどうかを示すブール値（デフォルトはfalse）。

# 戻り値

  * 各労働タイプの労働需要を表す配列。
