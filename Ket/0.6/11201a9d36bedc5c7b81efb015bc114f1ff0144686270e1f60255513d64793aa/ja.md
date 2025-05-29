```
schmidt_decomposition(ψ::AbstractVector, dims::AbstractVecOrTuple = _equal_sizes(ψ))
```

`ψ`のシュミット分解を生成し、サブシステムの次元は`dims`です。引数`dims`が省略された場合、同じサイズのサブシステムが仮定されます。返されるのは（ソートされた）シュミット係数λと、kron(U', V')*`ψ`がシュミット形式になるような等長写像U, Vです。

参考文献: [シュミット分解](https://en.wikipedia.org/wiki/Schmidt_decomposition)
