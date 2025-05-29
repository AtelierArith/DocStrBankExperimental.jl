```
ADAGRAD()
```

要素ごとの重みが二乗勾配の平均によって生成される[`SGD`](@ref)の変種です。

  * 参考: https://ruder.io/optimizing-gradient-descent/
  * 注: ADAGRADはOnlineStatsで学習率を使用しますが、これは通常の提示方法とは異なります。詳細についてはhttps://www.seqstat.com/post/adagrad/を参照してください。
