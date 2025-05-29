The complex is always stored this way

```
      maps[1]   maps[2]
    * ------> * ------> * ....
```

There are logically 2 types of complexes

  * chain
  * cochain

(stored in `typ` (`type` cannot be used as it is a keyword)

The type determines, jointly with `seed` the homological, external, numbering of the maps and object. `seed` always stores the logically minimal object index (in the sense of homological degree)

# Chain Complex

`typ == :chain`

The definition is `d_i(d_i+1(x)) = 0` where `d_i` are the (logically) numbered maps (differentials). The corresponding objects `M_i` are defined via

`d_i : M_i -> M_i-1`

Thus the minimal object (index) is the image of the last map =>   `maps[end] = d_seed+1`   `codomain(maps[end]) = M_seed`   `domain(maps[1]) = M_(seed+length(maps))`

# CoChain Complex

`typ == :cochain`

The definition is `d_i+1(d_i(x)) = 0` and

`d_i : M_i -> M_i+1`

The minimal object thus is `domain(maps[1]) = M_seed`, the largest thus `codomain(maps[end]) = M_(seed + length(maps))`

# Access

## range

the object - index - range is either

  * `(seed + length):-1:seed`     (chain complex)
  * `seed:(seed + length(maps))`  (cochain complex)

## map

map(C, i) =

  * `maps[length - (i - s)]`      (chain)
  * `maps[i-s]`                   (cochain)

## obj

`obj(C, i) = domain(map(C, i))` in both cases   BUT at the end, the last object is the codomain of the last map...
