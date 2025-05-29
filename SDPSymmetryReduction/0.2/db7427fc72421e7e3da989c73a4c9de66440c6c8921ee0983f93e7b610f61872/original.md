```
admissible_subspace([Partition{UInt16},] C, A, b[; verbose, atol])
```

Return the optimal admissible partition subspace for the semidefinite problem

> ```
>   minimize: ⟨Cᵀ, x⟩
> subject to: A·x = b
>             Mat(x) ⪰ 0
> ```


where `C` and `A` are symmetric.

The problem can be restricted to the subspace without changing its optimal value.

The partition is found by a Jordan-reduction algorithm saturating with **random** squares. With probability 1 the returned subspace is a Jordan algebra (i.e. closed under linear combinations and squaring). See Section 5.2 of Permenter thesis.

# Output

  * A `Partition` subspace `P`.
