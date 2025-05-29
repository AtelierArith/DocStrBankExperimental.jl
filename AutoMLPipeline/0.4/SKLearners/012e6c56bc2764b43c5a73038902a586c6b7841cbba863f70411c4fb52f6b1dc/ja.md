```
SKLearner(learner::String, args::Dict=Dict())
```

異なる機械学習モデルをロードするためのScikitlearnラッパーです。`sklearners()`を呼び出すと、利用可能な学習者のリストが表示されます。渡す引数についてはScikitlearnのドキュメントを参照してください。

`fit!`と`transform!`を実装しています。
