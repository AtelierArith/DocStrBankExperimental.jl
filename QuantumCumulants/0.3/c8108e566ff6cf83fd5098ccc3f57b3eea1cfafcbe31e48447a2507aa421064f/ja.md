```
DoubleIndexedVariable <: CNumber
DoubleIndexedVariable(name::Symbol,ind1::Index,ind2::Index;identical::Bool)
```

二重インデックスの記号変数。変数は（方程式が計算された後に）数値に簡単に置き換えることができます。参照: [`value_map`](@ref)

# フィールド:

  * name: 変数の名前を定義するシンボル
  * ind1: 変数の最初のインデックス
  * ind2: 変数の二番目のインデックス
  * identical: 変数が非ゼロの主対角項を持つことができるかどうかを定義するブール値。例えば: Γᵢᵢ ≠ 0 は true で指定されます。
