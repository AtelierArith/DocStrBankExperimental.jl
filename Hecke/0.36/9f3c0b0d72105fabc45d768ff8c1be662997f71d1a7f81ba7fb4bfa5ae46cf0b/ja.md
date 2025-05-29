```
trace_lattice_with_isometry(H::AbstractLat{T};
                            alpha::FieldElem = one(base_field(H)),
                            beta::FieldElem = gen(base_field(H)),
                            order::Integer = 2) where T  -> ZZLat, QQMatrix
```

与えられた格子 `H` は次のいずれかです：

  * $$
    \mathbb Z
    $$

    -格子（すなわち、`ZZLat` 型）；
  * CM 拡張 $E/K$ 上のエルミート格子で、$E/\mathbb{Q}$ は $p(0) = 1$ を満たす既約単項式 $p$ によって定義されます。

ペア $(L, f)$ を返します。ここで、$L$ は格子 $H$ のトレース格子として得られる $\mathbb{Z}$-格子 [`restrict_scalars(::AbstractLat)`](@ref) であり、$f$ は次のように与えられる $L$ の等距変換です：

  * $$
    H
    $$

    が `ZZLat` であり、`order == 1` の場合は恒等変換；
  * $$
    H
    $$

    が `ZZLat` であり、`order == 2` の場合は恒等変換の反対；
  * それ以外の場合は、ノルム 1 の $E$ の要素 `beta` による乗算によって与えられます。

オプション引数 `order` は、$H$ が $\mathbb Z$-格子でない場合には影響を与えません。

`alpha` の選択は、トレース構成のための $H$ 上の形式の再スケーリングの選択に対応し、[`restrict_scalars`](@ref) を使用します。

`beta` の選択は、エルミートの場合において、等距変換 `f` を構成するために使用される、$H$ の基底体のノルム 1 の要素の選択に対応します。

計算された等距変換 `f` は、格子 $H$ のトレース格子の周囲空間に対するその作用によって与えられます。
