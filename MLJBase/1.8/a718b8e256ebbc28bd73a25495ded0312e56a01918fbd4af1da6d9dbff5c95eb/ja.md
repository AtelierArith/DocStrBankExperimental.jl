```
nrows_at_source(N::node)
```

`N`のソースでラップされたデータの行数を返します。これはユニークであると仮定します。

`J = nrows(N)`とは混同しないでください。これは新しいノードであり、`J() = nrows(N())`となります。

参照：[ `nrows`](@ref)
