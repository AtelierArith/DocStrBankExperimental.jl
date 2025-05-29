```
iTpb
```

A composite recursive type of supertype `iT` representing a binary phylogenetic tree with no extinction and `λ` evolving as a Geometric Brownian motion  for `insane` use, with the following fields:

d1:  daughter tree 1   d2:  daughter tree 2   e:   edge   fx:  if fix tree   dt:  choice of time lag   fdt: final `δt`   lλ:  array of a Brownian motion evolution of `log(λ)`

```
iTpb()
```

Constructs an empty `iTpb` object.

```
iTpb(e::Float64)
```

Constructs an empty `iTpb` object with pendant edge `pe`.

```
iTpb(d1::iTpb, d2::iTpb, e::Float64)
```

Constructs an `iTpb` object with two `iTpb` daughters and pendant edge `pe`.
