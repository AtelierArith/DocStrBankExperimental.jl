```
err_segs(y_hat, y, l_segs; silent::Bool = true)
```

Remove mean error from multiple individual flight lines within larger dataset.

**Arguments:**

  * `y_hat`:  length-`N` prediction vector
  * `y`:      length-`N` target vector
  * `l_segs`: length-`N_lines` vector of lengths of `lines`, sum(l_segs) = `N`
  * `silent`: (optional) if true, no print outs

**Returns:**

  * `err`: length-`N` mean-corrected (per line) error
