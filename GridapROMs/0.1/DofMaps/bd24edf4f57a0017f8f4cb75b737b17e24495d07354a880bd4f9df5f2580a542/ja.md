```
fast_index(i,nfast::Integer) -> Any
```

テンソル積構造におけるファストインデックスを返します。サイズが `Ra × Ca` と `Rb × Rb` の2つの行列 `A` と `B` があるとします。これらのクロネッカー積 `AB = A ⊗ B` は、サイズ `RaRb × CaCb` であり、次のようにインデックス付けできます。

`AB[i,j] = A[slow_index(i,RbCb)] * B[fast_index(i,RbCb)]`、

ここで `nfast == RbCb` です。言い換えれば、この関数は `AB` に属するインデックスを `B` に属するインデックスに変換します。
