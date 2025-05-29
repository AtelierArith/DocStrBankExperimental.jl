```
sTpb
```

The simplest composite recursive type of supertype `sT` representing a binary phylogenetic tree for `insane` use, with the following fields:

d1: daughter tree 1   d2: daughter tree 2   e:  edge   fx: if fix

```
sTpb(e::Float64)
```

Constructs an empty `sTpb` object with edge `e`.

```
sTpb(d1::sTpb, d2::sTpb, e::Float64)
```

Constructs an `sTpb` object with two `sTpb` daughters and edge `e`.
