```
distinctiveness(s, corpus; [method=:dtw, dist=SqEuclidean(), radius=10, reduction=mean])
```

`s`の音響的独自性をコーパス`corpus`に基づいて計算します。`method`、`dist`、および`radius`引数は`acdist`に渡されます。`reduction`引数は、`mean`、`sum`、または`median`のように、反復可能なものを1つの数値に減らす任意の関数にすることができます。

詳細については、Kelley (2018年9月、音響的独自性が発話された単語認識に与える影響: パイロットスタディ、DOI: 10.7939/R39G5GV9Q) およびKelley & Tucker (2018年、音響距離を使用して語彙競争を定量化する、DOI: 10.7939/r3-wbhs-kr84)を参照してください。
