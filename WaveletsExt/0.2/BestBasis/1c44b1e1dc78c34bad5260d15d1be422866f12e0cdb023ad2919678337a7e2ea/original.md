```
tree_costs(X, method)
```

Returns the cost of each node in a binary tree in order to find the best basis.

# Arguments

  * `X::AbstractArray{T} where T<:AbstractFloat`: A set of decomposed signals, of sizes `(n,L,k)` for 1D signals or `(n,m,L,k)` for 2D signals, where:

      * `n`: Length of signal (1D) or vertical length of signal (2D).
      * `m`: Horizontal length of signal (2D).
      * `L`: Number of decomposition levels plus 1 (for standard wavelet decomposition) or   number of nodes in the tree (for redundant transforms such as ACWT and SWT).
      * `k`: Number of signals.
  * `method::BestBasisType`: Type of best basis, ie. `BB()`, `JBB()` or `LSDB()`.

!!! note
    For standard best basis (`BB()`), only one signal is processed each time, and therefore the inputs `X` should have dimensions `(n,L)` or `(n,m,L)` instead.


# Returns

  * `Vector{T}`: A vector containing the costs at each node.

# Examples

```julia
using Wavelets, WaveletsExt

X = generatesignals(:heavisine, 6) |> x -> duplicatesignals(x, 5, 2, true)
wt = wavelet(WT.db4)
Xw = wpdall(X, wt)

tree_costs(Xw, JBB())
tree_costs(Xw, LSDB())
```

**See also:** [`bestbasistree`](@ref), [`bestbasis_treeselection`](@ref)
