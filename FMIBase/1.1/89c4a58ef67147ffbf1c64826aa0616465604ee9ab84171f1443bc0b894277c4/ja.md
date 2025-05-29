```
getValueReferencesAndNames(obj; vrs=md.valueReferences)
```

with:

obj ∈ (fmi2ModelDescription, FMU2)

値参照とそれに対応する名前の辞書 `Dict(fmi2ValueReference, Array{String})` を返します。

# 引数

  * `md::fmi2ModelDescription`: モデル変数の静的情報を提供する構造体。

# キーワード

  * `vrs=md.valueReferences`: モデル記述の追加属性 `valueReferences::Array{fmi2ValueReference}` で、（基本型）変数値へのハンドルです。ハンドルと基本型は変数の値を一意に識別します。（デフォルト = `md.valueReferences::Array{fmi2ValueReference}`）

# 戻り値

  * `dict::Dict{fmi2ValueReference, Array{String}}`: fmi2ValueReference型のキーとArray{String}型の値を持つハッシュテーブルを構築する辞書を返します。
