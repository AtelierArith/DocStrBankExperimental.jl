```
    function BayesRCπ(pi,class,v,annot;estimatePi=false)
```

  * `pi` は各分散クラスのSNPの割合のベクトルです。`estimatePi=true` の場合、これは開始値としてのみ使用されます。
  * `class` は各分散クラスの一般的なSPN分散のスケールのベクトルです。スケールは増加順に並んでいる必要があります。例えば、[0.0,0.0001,0.001,0.01]。
  * `v` はSNPの事前分布の分散です。
  * `annnot` はアノテーションの行列です。行はSNP、列はアノテーションクラスです。エントリはバイナリでコーディングされており、0/1です。
  * `estimatePi` は `pi` が推定される場合は `true` です。デフォルトでは `false` です。
