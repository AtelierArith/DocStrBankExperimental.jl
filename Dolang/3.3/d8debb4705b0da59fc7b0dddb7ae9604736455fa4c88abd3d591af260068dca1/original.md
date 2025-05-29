```
stringify(var::Union{String,Symbol}, n::Integer)
```

stringify the string or symbol in the following way:

  * if `n >= 0` return `_var__n_`
  * if `n < 0` return `_var_mn_`
