```
getInputValueReferencesAndNames(md::fmi2ModelDescription)
```

入力の名前と値参照を持つ辞書を返します。

# 引数

  * `md::fmi2ModelDescription`: モデル変数の静的情報を提供する構造体。
  * `fmu::FMU2`: FMI 2.0.2標準におけるFMUとそのすべてのインスタンスを表す可変構造体。

# 戻り値

  * `dict::Dict{fmi2ValueReference, Array{String}}`: fmi2ValueReference型のキーとArray{String}型の値を持つハッシュテーブルを構築する辞書を返します。したがって、入力の名前と値参照を持つ辞書を返します。
