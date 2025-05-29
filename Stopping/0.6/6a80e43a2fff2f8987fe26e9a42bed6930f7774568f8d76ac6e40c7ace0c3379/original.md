```
`compress_state!(:: AbstractState; save_matrix :: Bool = false, max_vector_size :: Int = length(stateatx.x), pnorm :: Real = Inf, keep :: Bool = false, kwargs...)`
```

compress_state!: compress State with the following rules.

  * If it contains matrices and save_matrix is false, then the corresponding entries

are set to *init*field(typeof(getfield(stateatx, k)).

  * If it contains vectors with length greater than max*vector*size, then the

corresponding entries are replaced by a vector of size 1 containing its pnorm-norm.

  * If keep is true, then only the entries given in kwargs will be saved (the others are set to *init*field(typeof(getfield(stateatx, k))).
  * If keep is false and an entry in the State is in the kwargs list, then it is put as *init*field(typeof(getfield(stateatx, k)) if possible.

see also: `copy`, `copy_compress_state`, `ListofStates`
