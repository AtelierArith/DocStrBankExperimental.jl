```
LittleDict(keys, vals) <: AbstractDict
```

An ordered dictionary type for small numbers of keys. Rather than using `hash` or some other sophisticated measure to store the vals in a clever arrangement, it just keeps everything in a pair of lists.

While theoretically this has expected time complexity *O(n)* (vs the hash-based [`OrderedDict`](@ref)/`Dict`'s expected time complexity *O(1)*, and the search-tree-based `SortedDict`'s expected time complexity *O(log(n))*), in practice it is really fast, because it is cache & SIMD friendly.

It is reasonable to expect it to outperform an `OrderedDict`, with up to around 30 elements in general; or with up to around 50 elements if using a `LittleDict` backed by `Tuples` (see [`freeze`](@ref)) However, this depends on exactly how long `isequal` and `hash` take, as well as on how many hash collisions occur etc.

!!! note
    When constructing a `LittleDict` it is faster to pass in the keys and values each as seperate lists. So if you have them seperately already, do `LittleDict(ks, vs)` not `LittleDict(zip(ks, vs))`. Furthermore, key and value lists that are passed as `Tuple`s will not require any copies to create the `LittleDict`, so `LittleDict(ks::Tuple, vs::Tuple)` is the fastest constructor of all.

