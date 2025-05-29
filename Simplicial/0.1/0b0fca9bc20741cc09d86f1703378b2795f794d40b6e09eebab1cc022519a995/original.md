```
del(K, tau)
```

The deletion of `tau` from `K`. This is the set faces in `K` which are *not* cofaces of `tau`. Returned complex has same vertex type and vertex set as `K`.

$del_τ(K) = {σ ∈ K : τ ⊏̸ σ}$

For "deletion" in the sense "faces which do not intersect `tau`", compute the complement of `tau` in `K`'s vertex set and use `res` to restrict to that set.
