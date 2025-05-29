```
StopWhenSmallerOrEqual <: StoppingCriterion
```

変数が最小値以下になるとアルゴリズムが停止する停止基準のためのファンクタ。

# フィールド

  * `value`    アルゴリズムが停止するためにしきい値を下回る必要がある変数を格納します
  * `minValue` もし値がこのしきい値以下であればアルゴリズムが停止するしきい値を格納します

# コンストラクタ

```
StopWhenSmallerOrEqual(value, minValue)
```

`value`が`minValue`以下になると停止することを示すためにファンクタを初期化します。
