# グリュンワルド・レティニコフ感覚の乗法的および加法的近似

```
fracdiff(f, α, end_point, h, GLMultiplicativeAdditive())
```

グリュンワルド–レティニコフの乗法-加法-乗法-加法···法を用いて分数導関数を近似します。

### 例

```julia-repl
julia> fracdiff(x->x, 0.5, 1, 0.007, GLMultiplicativeAdditive())
1.127403405642918
```

```tex
@book{oldham_spanier_1984,
title={The fractional calculus: Theory and applications of differentiation and integration to arbitrary order},
author={Oldham, Keith B. and Spanier, Jerome},
year={1984}} 
```
