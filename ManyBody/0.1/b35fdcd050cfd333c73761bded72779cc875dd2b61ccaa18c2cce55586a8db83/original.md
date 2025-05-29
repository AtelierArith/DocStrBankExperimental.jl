Represent product of fermionic creation/annihilation operators.

For a Fock space of flavours, this is an abstract representation of the product of an arbitrary number of creation and annihilation operators, not necessarily normal ordered.  One can write each such product in a canonical form:

```
t(v,i,j,k) = v * prod(x -> c[x]', i) * prod(x -> c[x], reverse(j)) *
             prod(x -> c[x]*c[x]', k)
```

where `i`, `j` are tuples of flavours, each one ordered ascendingly, and `k` is a tuple of flavours disjoint from both `i` and `j`.  Note that above expression is not a normal-ordered product either, but a "classification" of each flavour with respect to the term's effect.

Instead of the `O(2^(2n))` dense or `O(2^n)` sparse storage required for the elements of such a product, this class stores only an `O(1)` set of bitfields allowing for fast on-the-fly computation.
