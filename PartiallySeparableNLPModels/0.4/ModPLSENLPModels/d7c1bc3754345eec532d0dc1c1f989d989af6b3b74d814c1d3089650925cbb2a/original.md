```
PLSENLPModel{G, T, S, M <: AbstractNLPModel{T, S}, Meta <: AbstractNLPModelMeta{T, S},} <: AbstractPQNNLPModel{T,S}
```

Deduct and allocate the partitioned structures of a NLPModel using a PLSE Hessian approximation. `PLSENLPModel` has fields:

  * `model`: the original model;
  * `meta`: gather information about the `PLSENLPModel`;
  * `counters`: count how many standards methods of `NLPModels` are called;
  * `n`: the size of the problem;
  * `N`: the number of element functions;
  * `vec_elt_fun`: a `ElementFunction` vector, of size `N`;
  * `M`: the number of distinct element-function expression trees;
  * `vec_elt_complete_expr_tree`: a `Complete_expr_tree` vector, of size `M`;
  * `element_expr_tree_table`: a vector of size `M`, the i-th element `element_expr_tree_table[i]::Vector{Int}` informs which element functions use the `vec_elt_complete_expr_tree[i]` expression tree;
  * `index_element_tree`: a vector of size `N` where each component indicates which `Complete_expr_tree` from `vec_elt_complete_expr_tree` is used for the corresponding element;
  * `vec_compiled_element_gradients`: the vector gathering the compiled tapes for every element gradient evaluations;
  * `op`: the partitioned matrix (main memory cost);
  * `name`: the name of partitioned quasi-Newton update performed
