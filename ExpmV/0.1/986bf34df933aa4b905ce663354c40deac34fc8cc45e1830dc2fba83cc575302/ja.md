```
expmv(t, A, b; <keyword arguments>)
```

行列ベクトル積 $exp(t A) b$ を返します。ここで `A` は $n × n$ のスパースな実数または複素数行列、`b` は $n$ の実数または複素数要素のベクトル、`t` はパラメータ（または値の範囲を表す `StepRangeLen` オブジェクト）です。

# 引数

  * `t`: `Number` または `StepRangeLen` オブジェクト
  * `A`: $n × n$ の実数または複素数のスパース行列
  * `b`: `n`-ベクトル
  * `M = []`: テイラー展開の次数を手動で設定
  * `precision = "double"`: `"double"`、`"single"` または `"half"` を指定可能。
  * `shift = false`: A のノルムを減少させるためにシフトを適用するには `true` に設定（論文のセクション 3.1 を参照）
  * `full_term = false`: 必要な精度に達したときに切り捨てるのではなく、完全なテイラー展開を評価するには `true` に設定
