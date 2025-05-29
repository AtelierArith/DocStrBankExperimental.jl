```
lr_mesolveProblem(
    H::QuantumObject{Operator},
    z::AbstractArray{T,2},
    B::AbstractArray{T,2},
    tlist::AbstractVector,
    c_ops::Union{AbstractVector,Tuple}=();
    e_ops::Union{AbstractVector,Tuple}=(),
    f_ops::Union{AbstractVector,Tuple}=(),
    opt::NamedTuple = lr_mesolve_options_default,
    kwargs...,
)
```

システムの低ランク時間発展のためのODE問題を定式化します。この関数は[`lr_mesolve`](@ref)によって呼び出されます。低ランクマスター方程式の詳細については、[gravina2024adaptive](@cite)を参照してください。

# 引数

  * `H::QuantumObject`: システムのハミルトニアン。
  * `z::AbstractArray`: 低ランクアルゴリズムの初期z行列。
  * `B::AbstractArray`: 低ランクアルゴリズムの初期B行列。
  * `tlist::AbstractVector`: 期待値と関数値が計算される時間ステップ。
  * `c_ops::Union{AbstractVector,Tuple}`: 崩壊演算子のリスト。
  * `e_ops::Union{AbstractVector,Tuple}`: 期待値が計算される演算子のリスト。
  * `f_ops::Union{AbstractVector,Tuple}`: 関数値が計算される関数のリスト。
  * `opt::NamedTuple`: 低ランクマスター方程式のオプション。
  * `kwargs`: 追加のキーワード引数。
