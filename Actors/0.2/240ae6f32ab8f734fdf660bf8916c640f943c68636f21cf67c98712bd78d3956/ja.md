```
become!(lk::Link, func, args1...; kwargs...)
become!(name::Symbol, ....)
```

アクターの動作を変更します。

# 引数

  * アクター `lk::Link`（または登録されている場合は `name::Symbol`）,
  * `func`: 呼び出し可能なオブジェクト,
  * `args1...`: `func` への（部分的な）引数,
  * `kwargs...`: `func` へのキーワード引数.
