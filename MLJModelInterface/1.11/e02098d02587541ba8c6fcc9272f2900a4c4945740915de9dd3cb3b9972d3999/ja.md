```
fitted_params(model, fitresult) -> human_readable_fitresult # named_tuple
```

モデルは `fitted_params` をオーバーロードすることがあります。フォールバックは `(fitresult=fitresult,)` を返します。

他のトレーニング関連の結果は、`fit` によって返されるタプルの `report` 部分に返されるべきです。
