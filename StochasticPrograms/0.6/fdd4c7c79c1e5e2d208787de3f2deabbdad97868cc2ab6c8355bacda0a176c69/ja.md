```
relax_integrality(stochasticprogram::StochasticProgram)
```

`stochasticprogram`を修正して、すべてのバイナリおよび整数制約を決定および補助変数に対して「緩和」します。

引数なしで呼び出すことができる関数を返し、元のstochasticprogramを復元します。この関数の動作は、その間に影響を受ける決定および変数に追加の変更が加えられた場合には未定義です。
