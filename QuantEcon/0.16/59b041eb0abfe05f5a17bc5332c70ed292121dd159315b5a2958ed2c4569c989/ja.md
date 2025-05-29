```
simplex_grid(m, n)
```

整数点からなる配列を構築します。(m-1)次元の単体 $\{x \mid x_1 + \cdots + x_m = n, x_i \geq 0\}$、または同等に、nのm部分構成が辞書順でリストされます。点の総数（したがって出力配列の長さ）は L = (n+m-1)!/(n!*(m-1)!) です（すなわち、(n+m-1) から (m-1) を選ぶ）。

# 引数

  * `m::Int` : 各点の次元。正の整数でなければなりません。
  * `n::Int` : 各点の座標の合計となる数。非負の整数でなければなりません。

# 戻り値

  * `out::Matrix{Int}` : 単体内の整数点を含む形状 (m, L) の配列で、辞書順に整列されています。

# 注意事項

各次元に沿ってn分割された(m-1)次元の*単位*単体のグリッドは、`simplex_grid(m, n) / n`によって得られます。

# 例

```julia
julia> simplex_grid(3, 4)
3×15 Matrix{Int64}:
 0  0  0  0  0  1  1  1  1  2  2  2  3  3  4
 0  1  2  3  4  0  1  2  3  0  1  2  0  1  0
 4  3  2  1  0  3  2  1  0  2  1  0  1  0  0
```

# 参考文献

A. Nijenhuis and H. S. Wilf, Combinatorial Algorithms, Chapter 5,    Academic Press, 1978.
