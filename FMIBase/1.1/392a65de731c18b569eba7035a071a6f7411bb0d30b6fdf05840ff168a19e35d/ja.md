```
getOutputValueReferencesAndNames(md::fmi2ModelDescription)
```

値参照とそれに対応する名前の辞書 `Dict(fmi2ValueReference, Array{String})` を返します。

# 引数

  * `md::fmi2ModelDescription`: モデル変数の静的情報を提供する構造体。

# キーワード

  * `vrs=md.outputvalueReferences`: モデル記述の追加属性 `outputvalueReferences::Array{fmi2ValueReference}` で、（基本型）変数値へのハンドルです。ハンドルと基本型は変数の値を一意に識別します。（デフォルト = `md.outputvalueReferences::Array{fmi2ValueReference}`）

# 返り値

  * `dict::Dict{fmi2ValueReference, Array{String}}`: fmi2ValueReference 型のキーと Array{String} 型の値を持つハッシュテーブルを構築する辞書を返します。したがって、（vrs、出力の名前）を持つ辞書を返します。
