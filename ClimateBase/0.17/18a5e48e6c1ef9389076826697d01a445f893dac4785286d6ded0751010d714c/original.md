```
value_space(A, B; Arange) → Bmeans, bin_indices
```

Express the array `B` into the value space of `A`. `B, A` must have the same indices. This means that `A` is binned according to the given `Arange`, and the same indices that binned `A` are also used to bin `B`. The `i`-th bin contains data whose `A` values ∈ [`Arange[i]`, `Arange[i+1]`). In each bin, the binned values of `B` are averaged, resulting in `Bmeans`.

Elements of `A` that are not ∈ `Arange` are skipped. The returned `bin_indices` are the indices in each bin (hence, the weights for the means are just `length.(bin_indices)`)

By default `Arange = range(minimum(A), nextfloat(maximum(A)); length = 100)`.
