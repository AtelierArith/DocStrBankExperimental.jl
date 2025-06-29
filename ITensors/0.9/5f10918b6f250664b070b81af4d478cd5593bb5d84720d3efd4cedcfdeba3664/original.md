```
combiner(inds::Indices; kwargs...)
```

Make a combiner ITensor which combines the indices (of type Index) into a single, new Index whose size is the product of the indices given. For example, given indices `i1,i2,i3` the combiner will have these three indices plus an additional one whose dimension is the product of the dimensions of `i1,i2,i3`.

Internally, a combiner ITensor uses a special storage type which means it does not hold actual tensor elements but just information about how to combine the indices into a single Index. Taking a product of a regular ITensor with a combiner uses special fast algorithms to combine the indices.

To obtain the new, combined Index that the combiner makes out of the indices it is given, use the `combinedind` function.

To undo or reverse the combining process, uncombining the Index back into the original ones, contract the tensor having the combined Index with the conjugate or `dag` of the combiner. (If the combiner is an ITensor `C`, multiply by `dag(C)`.)

### Example

```
# Combine indices i and k into a new Index ci
T = random_itensor(i,j,k)
C = combiner(i,k)
CT = C * T
ci = combinedind(C)

# Uncombine ci back into i and k
TT = dag(C) * CT

# TT will be the same as T
@show norm(TT - T) ≈ 0.0
```

```
          i  j  k
          |  |  |
 T   =    =======

          ci  i  k
          |   |  |
 C   =    ========

          ci  j
          |   |
 C * T =  =====
```
