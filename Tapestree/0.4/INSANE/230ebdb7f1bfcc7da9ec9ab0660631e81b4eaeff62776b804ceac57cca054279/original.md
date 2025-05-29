```
sTf_label
```

A composite recursive type of supertype `sT` representing a labelled binary phylogenetic tree with fossils for `insane` use, with the following fields:

d1: daughter tree 1   d2: daughter tree 2   e:  edge   iμ: if it is extinct   iψ: if it is a fossil   l:  label

```
sTf_label(e::Float64, iμ::Bool, iψ::Bool, l::String)
```

Constructs an empty `sTf_label` object with edge `e` and label `l`.

```
sTf_label(d1::sTf_label e::Float64, l::String)
```

Constructs an `sTf_label` object with one `sTf_label` daughter and edge `e`.

```
sTf_label(d1::sTf_label, d2::sTf_label, e::Float64, l ::String)
```

Constructs an `sTf_label` object with two `sTf_label` daughters and edge `e`.
