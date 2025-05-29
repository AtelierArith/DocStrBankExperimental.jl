```
KrylovConstructor(vm; vm_empty=vm)
KrylovConstructor(vm, vn; vm_empty=vm, vn_empty=vn)
```

Krylov methods require a workspace containing vectors of length `m` and `n` to solve linear problems of size `m × n`. The `KrylovConstructor` facilitates the allocation of these vectors using `similar`.

For square problems (`m == n`), use the first constructor with a single vector `vm`. For rectangular problems (`m ≠ n`), use the second constructor with `vm` and `vn`.

#### Input arguments

  * `vm`: a vector of length `m`;
  * `vn`: a vector of length `n`.

#### Keyword arguments

  * `vm_empty`: an empty vector that may be replaced with a vector of length `m`;
  * `vn_empty`: an empty vector that may be replaced with a vector of length `n`.

#### Note

Empty vectors `vm_empty` and `vn_empty` reduce storage requirements when features such as warm-start or preconditioners are unused. These empty vectors will be replaced within a [`KrylovWorkspace`](@ref) only if required, such as when preconditioners are provided.
