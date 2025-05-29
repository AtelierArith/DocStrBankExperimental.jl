最適化するためのエッジごとの目的関数。これらの値はネイティブにサポートされています：

  * `Load`: 各エッジの負荷が考慮されます。
  * `KleinrockLoad`: 負荷に対してKleinrock関数が適用されます。
  * `FortzThorupLoad`: 負荷に対してFortz-ThorupのKleinrock関数の線形化が適用されます。

Kleinrock関数は次のように定義されます：

$$
K(x) = \frac{x}{1-x}
$$
