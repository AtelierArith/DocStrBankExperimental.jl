```
margProdLaborGeneral(labor_input::Union{AbstractArray{<:Real}, Nothing}, z::Real, b_g::Function, e_h::Vector{Function}; xT=nothing, q=nothing) -> AbstractArray{<:Real}
```

労働者タイプごとの限界生産性を入力パラメータに基づいて計算します。

# 引数

  * `labor_input`: H要素を持つ異なるタイプの労働入力の配列。`nothing`の場合、xTとqに基づいて内部で計算されます。
  * `z`: 生産性スカラー。
  * `b_g`: タスク密度関数。
  * `e_h`: 比較優位関数のベクトル。
  * `xT`: (オプション) 事前に計算されたタスク閾値を表す配列。提供されない場合、関数内で計算されます。
  * `q`: (オプション) 事前に計算された生産量を表すスカラー。提供されない場合、関数内で計算されます。

# 戻り値

  * 各労働者タイプの限界生産性を表す配列。

`labor_input`が提供されない場合、他のパラメータに基づいて`q`と`unitInputDemand_general`関数を使用して計算されます。
