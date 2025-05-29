# Grünwald Letnikov sense Multiplicative and Addtive approximation

```
fracdiff(f, α, end_point, h, GLMultiplicativeAdditive())
```

Grünwald–Letnikov multiplication-addition-multiplication-addition··· method to approximate fractional derivative.

### Example

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
