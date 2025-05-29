```
mpar(; kwargs...)
```

`kwargs`で定義されたパラメータ値のすべての組み合わせを持つタプルを返します。キーワード引数:

  * `kwargs` : パラメータの値のベクトル。

## 例

```julia
using Jchemo
nlvdis = 25 ; metric = [:mah] 
h = [1 ; 2 ; Inf] ; k = [500 ; 1000] 
pars = mpar(nlvdis = nlvdis, metric = metric, h = h, k = k) 
length(pars[1])
reduce(hcat, pars)
```
