```
@evaltest_throw "$code" begin $tests end
@evaltest_throw raw"$code" begin $tests end
```

`code`を評価し、スローされた例外を変数`ans`に割り当て、その後`tests`を実行します。

このマクロは`LiterateTest.preprocess`によって処理されることを意図しています。
