# カプート感覚ダイエトヘルム計算

```
fracdiff(f, α, end_point, h, CaputoDiethelm())
```

積分の微分を近似するために、（積の台形法から導出された）数値重みを使用します。

### 例

```julia-repl
julia> fracdiff(x->x, 0.5, 1, 0.007, CaputoDiethelm())
1.128378318687192
```

!!! info "範囲"
    0 < α < 1


ダイエトヘルムの方法は、[積の台形法](https://en.wikipedia.org/wiki/Trapezoidal_rule)と[リチャードソン外挿法](https://en.wikipedia.org/wiki/Richardson_extrapolation)を使用して、カプート感覚の分数微分を計算します。

```tex
@article{10.1093/imanum/17.3.479,
author = {DIETTELM, KAI},
title = "{有限部分積分のための一般化された複合数値公式}",
journal = {IMA Journal of Numerical Analysis},
doi = {10.1093/imanum/17.3.479},
}
```
