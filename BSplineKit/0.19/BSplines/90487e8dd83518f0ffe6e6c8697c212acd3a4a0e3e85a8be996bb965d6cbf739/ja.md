```
nonzero_in_segment(B::AbstractBSplineBasis, n::Int) -> UnitRange{Int}
```

指定されたノットセグメントで非ゼロの基底関数の範囲を返します。

$$
n
$$

-番目のノットセグメントは$Ω_n = [t_n, t_{n + 1}]$によって定義されます。

[`BSplineBasis`](@ref)および`RecombinedBSplineBasis`の場合、任意の指定されたセグメント内の非ゼロ関数の数は一般的にBスプラインの次数$k$に等しいです。この数は境界付近で減少しますが、Bスプラインのノットがそこに重複度$k$を持つ場合（デフォルトとして）、これは重要ではありません。

Bスプライン基底の場合、境界を除けば、非ゼロのBスプラインは$\left\{ b_i \right\}_{i = n - k + 1}^{n}$です。したがって、この関数は`B`が`BSplineBasis`であるときに`(n - k + 1):N`を返します。

逆の操作については[`support`](@ref)も参照してください。
