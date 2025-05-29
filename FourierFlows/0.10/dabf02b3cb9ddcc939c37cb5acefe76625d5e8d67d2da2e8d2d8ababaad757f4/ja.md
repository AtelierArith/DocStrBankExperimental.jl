```
struct Output
```

出力のための複合型。

  * `prob::FourierFlows.Problem`: 出力に関連する問題
  * `path::String`: 出力ファイルのパス
  * `fields::Dict{Symbol, Function}`: 保存されるフィールド; この診断に関連する問題
