```
sT_label
```

A composite recursive type of supertype `sT` representing a labelled binary phylogenetic tree for `insane` use, with the following fields:

d1: daughter tree 1   d2: daughter tree 2   e:  edge   l:  label

```
sT_label()
```

Constructs an empty `sT_label` object.

```
sT_label(e::Float64)
```

Constructs an empty `sT_label` object with edge `e`.

```
sT_label(d1::sT_label, d2::sT_label, e::Float64)
```

Constructs an `sT_label` object with two `sT_label` daughters and edge `e`.
