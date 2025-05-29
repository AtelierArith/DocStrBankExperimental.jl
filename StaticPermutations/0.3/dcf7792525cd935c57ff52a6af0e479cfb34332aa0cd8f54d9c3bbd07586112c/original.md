```
Permutation{p} <: AbstractPermutation
```

Describes a compile-time dimension permutation.

The type parameter `p` should be a valid permutation such as `(3, 1, 2)`.

---

```
Permutation(perm::Vararg{Int})
Permutation(perm::NTuple{N,Int})
```

Constructs a `Permutation`.

# Example

Both are equivalent:

```julia
p1 = Permutation(3, 4)
p2 = Permutation((3, 4))
```
