```
@replicate n expr
```

Replicate the expression `n` times

## Example

```julia
using DataConvenience, Random
@replicate 10 randstring(8) # returns 10 random length 8 strings
```
