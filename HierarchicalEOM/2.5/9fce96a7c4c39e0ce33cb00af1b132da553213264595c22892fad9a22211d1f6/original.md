```
struct Nvec
```

An object which describes the repetition number of each multi-index ensembles in auxiliary density operators.

The `n_vector` ($\vec{n}$) denotes a set of integers:

$$
\{ n_{1,1}, ..., n_{\alpha, k}, ... \}
$$

associated with the $k$-th exponential-expansion term in the $\alpha$-th bath. If $n_{\alpha, k} = 3$ means that the multi-index ensemble $\{\alpha, k\}$ appears three times in the multi-index vector of ADOs (see the notations in our paper).

The hierarchy level ($L$) for an `n_vector` is given by $L=\sum_{\alpha, k} n_{\alpha, k}$

# Fields

  * `data` : the `n_vector`
  * `level` : The level `L` for the `n_vector`

# Methods

One can obtain the repetition number for specific index (`idx`) by calling : `n_vector[idx]`. To obtain the corresponding tuple $(\alpha, k)$ for a given index `idx`, see `bathPtr` in [`HierarchyDict`](@ref) for more details.

`HierarchicalEOM.jl` also supports the following calls (methods) :

```julia
length(n_vector);  # returns the length of `Nvec`
n_vector[1:idx];   # returns a vector which contains the excitation number of `n_vector` from index `1` to `idx`
n_vector[1:end];   # returns a vector which contains all the excitation number of `n_vector`
n_vector[:];       # returns a vector which contains all the excitation number of `n_vector`
from n in n_vector  # iteration
    # do something
end
```
