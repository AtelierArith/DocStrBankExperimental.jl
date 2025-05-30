```
reduce_problem(::Type{R}, problem::AbstractProblem, reducer::AbstractReducer) where R
```

問題のサイズを直接縮小します。例えば、グラフ書き換えによってです。これは、縮小と分岐戦略において重要なステップです。

### 引数

  * `R`: 解のサイズを計算するために使用される要素型。加法的可換モノイド構造を持っている必要があります。
  * `problem`: 問題のインスタンス。
  * `reducer`: リデューサー。

### 戻り値

2つの値のタプル：

  * `AbstractProblem`: 縮小されたサイズの新しい`AbstractProblem`のインスタンス。
  * `Number`: 縮小のローカルゲインで、グローバルゲインに加算されます。
