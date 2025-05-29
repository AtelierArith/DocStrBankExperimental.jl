```
fmi2GetStateValueReferencesAndNames(md::fmi2ModelDescription)
```

状態値参照とそれに対応する名前の辞書 `Dict(fmi2ValueReference, Array{String})` を返します。

# 引数

  * `md::fmi2ModelDescription`: モデル変数の静的情報を提供する構造体。

# 戻り値

  * `dict::Dict{fmi2ValueReference, Array{String}}`: fmi2ValueReference 型のキーと Array{String} 型の値を持つハッシュテーブルを構築する辞書を返します。したがって、(vrs, 状態の名前) の辞書を返します。
