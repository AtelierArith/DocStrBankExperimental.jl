```
bestbasistreeall(X, method)
```

Compute the standard best basis tree of a set of signals.

# Arguments

  * `X::AbstractArray{T} where T<:AbstractFloat`: A set of decomposed signals, of sizes `(n,L,k)` for 1D signals or `(n,m,L,k)` for 2D signals, where:

      * `n`: Length of signal (1D) or vertical length of signal (2D).
      * `m`: Horizontal length of signal (2D).
      * `L`: Number of decomposition levels plus 1 (for standard wavelet decomposition) or   number of nodes in the tree (for redundant transforms such as ACWT and SWT).
      * `k`: Number of signals.
  * `method::BB`: Standard best basis method, eg. `BB()`.

# Returns

  * `::BitMatrix`: `(nₜ,k)` matrix where each column corresponds to a tree.

# Examples

```julia
using Wavelets, WaveletsExt

X = generatesignals(:heavisine, 6) |> x -> duplicatesignals(x, 5, 2, true)
wt = wavelet(WT.db4)

Xw = wpdall(X, wt)
bestbasistreeall(Xw, BB())

Xw = swpdall(X, wt)
bestbasistree(Xw, BB(redundant=true))
```

**See also:** [`bestbasistree`](@ref)
