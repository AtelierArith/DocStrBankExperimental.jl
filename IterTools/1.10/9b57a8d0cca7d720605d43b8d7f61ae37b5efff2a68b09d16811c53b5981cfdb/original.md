```
cache(it)
```

Cache the elements of an iterator so that subsequent iterations are served from the cache.

```jldoctest
julia> c = cache(Iterators.map(println, 1:3));

julia> collect(c);
1
2
3

julia> collect(c);

```

Be aware that if iterating the original  has a side-effect it will not be repeated when iterating again,  – indeed that is a key feature of the `CachedIterator`. Be aware also that if the original iterator is nondeterminatistic in its order, when iterating again from the cache it will infact be determinatistic and will be the same order as before – this also is a feature.
