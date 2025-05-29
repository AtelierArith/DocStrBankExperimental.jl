```
profile(m::Minuit, var; size=100, bound=2, grid=nothing, subtract_min=false)
```

範囲にわたる1Dコスト関数プロファイルを計算します。

最小値の周りのコスト関数の1Dスキャンで、最小値を検査するのに役立ちます。複数の自由パラメータを持つフィットの場合、これは`mncontour`によって計算されるMinosプロファイルとは異なります。

## 引数

  * `m::Minuit` : 最小化するMinuitオブジェクト。
  * `var` : スキャンするパラメータ（名前またはインデックス）。
  * `size=100` : スキャンポイントの数。`grid`が設定されている場合は無視されます。
  * `bound=2` : 最小値の周りを対称的にスキャンする`sigma`の数。`grid`が設定されている場合は無視されます。
  * `grid::AbstractVector` : スキャンするグリッドポイント。`grid`が設定されている場合、`size`と`bound`は無視されます。
  * `subtract_min::Bool=false` : 戻り値から最小値を引きます。

## 戻り値

  * Tuple(`x`, `y`) : パラメータ値と関数値の1D配列のタプル。
