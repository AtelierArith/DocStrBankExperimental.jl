```
infer(GibbsSampling, state::Assignment, InferenceState)
```

`N` 回のイテレーションのためにギブスサンプリングを実行します。各イテレーションは1つのノードを変更します。

最初の `burn_in` サンプルを破棄し、`thin` 番目のサンプルのみを保持します。例えば、`thin=3` の場合、最初の2つのサンプルを破棄し、3番目を保持します。
