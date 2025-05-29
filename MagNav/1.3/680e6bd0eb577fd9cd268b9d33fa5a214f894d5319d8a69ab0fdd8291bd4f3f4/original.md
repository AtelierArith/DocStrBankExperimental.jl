```
chunk_data(x, y, l_window::Int)
```

Break data into non-overlapping sequences (vectors).

**Arguments:**

  * `x`:        `N` x `Nf` data matrix (`Nf` is number of features)
  * `y`:        length-`N` target vector
  * `l_window`: temporal window length

**Returns:**

  * `x_seqs`: sequence (vector) of `Nf` x `l_window` data matrices
  * `y_seqs`: sequence (vector) of length-`l_window` target vectors
