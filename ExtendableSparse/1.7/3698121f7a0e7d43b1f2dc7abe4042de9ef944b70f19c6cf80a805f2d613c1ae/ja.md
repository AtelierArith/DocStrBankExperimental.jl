```
eliminate_dirichlet!(A,dirichlet_marker)
```

行列内のディリクレノードを削除するには、次のように設定します。

```julia
    A[:,i]=0; A[i,:]=0; A[i,i]=1
```

ディリクレとしてマークされたノード `i` に対して。

Aを返します。
