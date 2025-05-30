```
measure(problem::AbstractProblem, measure::AbstractMeasure)::Number
```

問題のサイズを計算し、分岐戦略の指針となるように縮小します。

### 引数

  * `problem`: 問題のインスタンス。
  * `measure`: 問題のサイズの測定。

### 戻り値

問題のサイズを表す実数。
