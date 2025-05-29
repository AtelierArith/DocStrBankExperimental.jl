```
optimize_code(eincode, size_dict, optimizer = GreedyMethod(), simplifier=nothing, permute=true) -> optimized_eincode
```

Optimize the einsum contraction code and reduce the time/space complexity of tensor network contraction. Returns a `NestedEinsum` instance. Input arguments are

  * `eincode` is an einsum contraction code instance, one of `DynamicEinCode`, `StaticEinCode` or `NestedEinsum`.
  * `size` is a dictionary of "edge label=>edge size" that contains the size information, one can use `uniformsize(eincode, 2)` to create a uniform size.
  * `optimizer` is a `CodeOptimizer` instance, should be one of `GreedyMethod`, `Treewidth`, `KaHyParBipartite`, `SABipartite` or `TreeSA`. Check their docstrings for details.
  * `simplifier` is one of `MergeVectors` or `MergeGreedy`.
  * optimize the permutation if `permute` is true.

### Examples

```jldoctest
julia> using OMEinsum

julia> code = ein"ij, jk, kl, il->"
ij, jk, kl, il -> 

julia> optimize_code(code, uniformsize(code, 2), TreeSA());
```
