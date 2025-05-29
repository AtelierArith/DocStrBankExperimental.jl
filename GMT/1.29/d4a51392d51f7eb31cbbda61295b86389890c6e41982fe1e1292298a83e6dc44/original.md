```
u, ind = gunique(x::AbstractVector; sorted=false)
```

Return an array containing only the unique elements of `x` and the indices `ind` such that `u = x[ind]`. If `sorted` is true the output is sorted (default is not)

```
u, ic, ia = gunique(x::AbstractMatrix; sorted::Bool=false, rows=true)
```

Behaves like Matlab's unique(x, 'rows'), where u = x(ia,:) and x = u(ic,:). If `rows` is false then `ic` is empty.
