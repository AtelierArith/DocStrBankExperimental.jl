```
@evaltest "$code" begin $tests end
@evaltest raw"$code" begin $tests end
```

`code`を評価し、変数`ans`に割り当ててから、`tests`を実行します。

このマクロは`LiterateTest.preprocess`によって処理されることを意図しています。
