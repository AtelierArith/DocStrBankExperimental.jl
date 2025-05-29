```
products(tns, dim)
```

`ProductArray`を作成します。

```
    products(tns, dim)[i...] == tns[i[1:dim-1]..., i[dim] * i[dim + 1], i[dim + 2:end]...]
```

これは[`toeplitz`](@ref)のようですが、プラスの代わりに掛け算を使用しています。
