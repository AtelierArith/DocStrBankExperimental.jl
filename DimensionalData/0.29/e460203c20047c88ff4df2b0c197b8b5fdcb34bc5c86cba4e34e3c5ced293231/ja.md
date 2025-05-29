```
seasons(; [start=Dates.December, labels])
```

3か月の期間のための`CyclicBins`を生成します。

## キーワード

  * `start`: デフォルトでは季節は12月に始まりますが、任意の整数`1:12`を使用できます。
  * `labels`: 4つのラベルのベクトル、または選択された四半期の`Vector{Int}`からラベルを生成する関数です。
