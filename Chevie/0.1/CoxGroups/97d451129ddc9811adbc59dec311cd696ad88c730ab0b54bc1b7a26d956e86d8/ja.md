`longest(W)`

もし `W` が有限であれば、コクセター群 `W` の最大長の一意の要素を返します。それ以外の場合は無限にループする可能性があります。

```julia-repl
julia> longest(coxsym(4))
(1,4)(2,3)
```

`longest(W,I)`

インデックス `I` の生成反射によって生成される `W` の放物群の最長要素を返します。

```julia-repl
julia> longest(coxsym(4))
(1,4)(2,3)
```
