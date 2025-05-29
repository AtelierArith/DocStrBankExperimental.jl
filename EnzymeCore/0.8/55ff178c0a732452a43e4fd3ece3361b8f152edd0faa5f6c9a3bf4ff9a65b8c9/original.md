```
DuplicatedNoNeed(x, ∂f_∂x)
```

Like [`Duplicated`](@ref), except also specifies that Enzyme may avoid computing the original result and only compute the derivative values. This creates opportunities for improved performance.

```julia

function square_byref(out, v)
    out[] = v * v
    nothing
end

out = Ref(0.0)
dout = Ref(1.0)
Enzyme.autodiff(Reverse, square_byref, DuplicatedNoNeed(out, dout), Active(1.0))
dout[]

# output
0.0
```

For example, marking the out variable as `DuplicatedNoNeed` instead of `Duplicated` allows Enzyme to avoid computing `v * v` (while still computing its derivative).

This should only be used if `x` is a write-only variable. Otherwise, if the differentiated function stores values in `x` and reads them back in subsequent computations, using `DuplicatedNoNeed` may result in incorrect derivatives. In particular, `DuplicatedNoNeed` should not be used for preallocated workspace, even if the user might not care about its final value, as marking a variable as NoNeed means that reads from the variable are now undefined.
