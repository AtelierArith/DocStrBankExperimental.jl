```
sTbd
```

The simplest composite recursive type of supertype `sT` representing a binary phylogenetic tree for `insane` use, with the following fields:

d1: daughter tree 1   d2: daughter tree 2   e:  edge   iμ: is an extinction node   fx: if it is fix

```
sTbd(e::Float64)
```

Constructs an empty `sTbd` object with edge `e`.

```
sTbd(d1::sTbd, d2::sTbd, e::Float64)
```

Constructs an `sTbd` object with two `sTbd` daughters and edge `e`.
