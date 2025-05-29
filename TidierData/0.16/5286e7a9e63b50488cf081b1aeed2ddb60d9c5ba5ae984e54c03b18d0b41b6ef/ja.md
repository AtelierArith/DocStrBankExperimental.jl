```
TidierData_set(option::AbstractString, value::Bool)
```

パッケージオプションを設定します。

サポートされているオプションとその機能は次のとおりです：

  * "code": デフォルトは `false`。`true` に設定すると、このオプションは TidierData.jl パッケージによって生成された DataFrames.jl コードを表示します。これは、TidierData.jl によって生成されたコードによってエラーが導入されているかどうかをデバッグするのに役立ちます。

# 引数

  * `option`: "code"
  * `value`: `true` または `false`
