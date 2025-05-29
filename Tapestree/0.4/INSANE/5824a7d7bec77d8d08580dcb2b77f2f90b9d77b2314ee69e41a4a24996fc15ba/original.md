```
sTfbd
```

The simplest composite recursive type of supertype `sTf` representing a binary phylogenetic tree for `insane` use, with the following fields:

d1: daughter tree 1   d2: daughter tree 2   e:  edge   iμ: is an extinction node   iψ: is a fossil node   fx: if it is fix

```
sTfbd(e::Float64)
```

Constructs an empty `sTfbd` object with edge `e`.

```
sTfbd(d1::sTfbd, d2::sTfbd, e::Float64)
```

Constructs an `sTfbd` object with two `sTfbd` daughters and edge `e`.

```
sTfbd(d1::sTfbd, e::Float64)
```

Constructs an `sTfbd` object with one sampled ancestor, one `sTfbd` daughter and edge `e`.
