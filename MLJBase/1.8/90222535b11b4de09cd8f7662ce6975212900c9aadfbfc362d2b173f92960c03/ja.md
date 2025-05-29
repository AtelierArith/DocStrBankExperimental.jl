```
default_logger(logger)
```

デフォルトのロガーをリセットします。

# 例

ローカルサーバーの `http://127.0.0.1:500` で [MLflow](https://mlflow.org/docs/latest/index.html) トラッキングサービスが実行されているとします。`logger` が指定されていないすべての `evaluate` 呼び出しでは、パフォーマンス評価が自動的にサービスにログされます。以下のように：

```julia
using MLJ
logger = MLJFlow.Logger("http://127.0.0.1:5000/api")
default_logger(logger)

X, y = make_moons()
model = ConstantClassifier()
evaluate(model, X, y, measures=[log_loss, accuracy)])
```
