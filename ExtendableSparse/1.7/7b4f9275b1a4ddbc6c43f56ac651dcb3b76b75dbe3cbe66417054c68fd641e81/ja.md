```
eliminate_dirichlet(A,dirichlet_marker)
```

Aのスパースパターンを共有するコピーBを作成します。DirichletノードをBから排除するために、次のように設定します。

```julia
    B[:,i]=0; B[i,:]=0; B[i,i]=1
```

Dirichletとしてマークされたノード`i`について。

Bを返します。
