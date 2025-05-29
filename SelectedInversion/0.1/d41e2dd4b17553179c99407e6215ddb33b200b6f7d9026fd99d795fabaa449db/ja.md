```
SupernodalMatrix
```

スパースブロック下三角行列をスーパーノードレイアウトで表します。スーパーノードは、上部の三角ブロックの下に同一のスパースパターンを持つ連続した列のセットです。各スーパーノードに対して、対応する非ゼロエントリは密なチャンクに格納されます。これにより、これらのチャンクに対してBLASを使用することができ、スパース行列と密行列の強みを組み合わせることができます。

# フィールド

  * `N::Int`: 行数
  * `M::Int`: 列数
  * `n_super::Int`: スーパーノードの数
  * `super_to_col::Vector{Int}`: 各スーパーノードの開始/終了列。                              長さ `n_super + 1`。
  * `col_to_super::Vector{Int}`: 各列をそのスーパーノードインデックスにマッピングします。                              長さ `M`。
  * `super_to_vals::Vector{Int}`: `vals`内の各スーパーノードの開始/終了インデックス。                               長さ `n_super + 1`。
  * `super_to_rows::Vector{Int}`: `rows`内の各スーパーノードの開始/終了インデックス。                               長さ `n_super + 1`。
  * `vals::Vector{Float64}`: 非ゼロ値。
  * `rows::Vector{Int}`: 行インデックス。注意: これらはゼロインデックスです！
  * `max_super_rows::Int`: スーパーノードチャンク内の三角ブロックの下にある最大行数。
  * `transposed_chunks::Bool`: チャンクの転置を格納するかどうか、すなわち                            チャンク内の最初の軸がスーパーノードの列に対応するかどうか。
  * `symmetric_access::Bool`: エントリにアクセスする際に対称性を強制するかどうか。
  * `invperm::Vector{Int}`: エントリにアクセスする前に適用する置換                         `depermuted_access == true` の場合。
  * `depermuted_access::Bool`: エントリにアクセスする前に逆置換を適用するかどうか。
