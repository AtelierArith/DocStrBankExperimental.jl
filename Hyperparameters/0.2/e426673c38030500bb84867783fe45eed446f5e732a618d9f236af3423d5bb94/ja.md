```
hyperparam([T::Type,] name; prefix="SM_HP_"))
```

与えられた `name` から、名前が大文字で、`prefix` で接頭辞が付けられた環境変数からハイパーパラメータをロードします。型 `T` が渡された場合は、その型として解析されます。そうでない場合は、`Bool`、`Int`、次に `Float`、最後に `String` の中から最初に成功したものを推測します。

また、ハイパーパラメータとその値をグローバルな `HYPERPARAMETERS` 辞書に保存します。この関数は一般的に SageMaker と一緒に使用されることが期待されており、そのためのデフォルトの接頭辞を提供します。

```jldoctest
using Hyperparameters
ENV["HP_POWER_LEVEL"] = "9001"
hyperparam(:power_level; prefix="HP_")

# output
9001.0
```
