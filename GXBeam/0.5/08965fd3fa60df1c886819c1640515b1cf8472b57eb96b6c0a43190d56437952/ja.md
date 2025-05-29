```
AssemblyState{TF, TP<:AbstractVector{PointState{TF}}, TE<:AbstractVector{ElementState{TF}}}
```

アセンブリ内のポイントと要素の状態変数を格納するための構造体。

# フィールド:

  * `points::TP`: アセンブリ内の各ポイントに対する[`PointState`](@ref)の配列
  * `elements::TE`: アセンブリ内の各要素に対する[`ElementState`](@ref)の配列
