```
margProdLabor(labor_input::Union{AbstractArray{<:Real}, Nothing}, θ::Real, κ::Real, z::Real, αVec::AbstractArray{<:Real}; xT=nothing, q=nothing) -> AbstractArray{<:Real}
```

労働者タイプごとの労働の限界生産性を入力パラメータに基づいて計算します。

# 引数

  * `labor_input`: 労働需要の値の配列。`nothing`の場合、内部で計算されます（xTとqが与えられた場合）。
  * `θ`: ブループリントのスケールパラメータ。
  * `κ`: ブループリントの形状パラメータ。
  * `z`: 生産性パラメータ。
  * `αVec`: 比較優位の値の配列。
  * `xT`: （オプション）事前に計算されたタスクの閾値を表す配列。提供されない場合、関数内で計算されます。
  * `q`: （オプション）事前に計算された生産量を表すスカラー。提供されない場合、関数内で計算されます。

# 戻り値

  * 各労働者タイプの労働の限界生産性を表す配列。

`labor_input`が提供されない場合、他のパラメータに基づいて`q`と`unitInputDemand`関数を使用して計算されます。
