```
SemiInfiniteVariable{I <: GeneralVariableRef} <: JuMP.AbstractVariable
```

半無限変数を格納するための `DataType` で、部分的に無限変数をサポートします。

**フィールド**

  * `infinite_variable_ref::I`: 元の無限/導関数変数。
  * `eval_supports::Dict{Int, Float64}`: 評価サポートに対する元のパラメータタプルの線形インデックス。
  * `parameter_nums::Vector{Int}`: 評価された `parameter_refs` に関連するパラメータ番号。
  * `object_nums::Vector{Int}`: 評価された `parameter_refs` に関連するパラメータオブジェクト番号。
