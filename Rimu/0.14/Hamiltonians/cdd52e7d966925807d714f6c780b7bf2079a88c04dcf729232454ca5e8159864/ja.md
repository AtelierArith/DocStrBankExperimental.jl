```
fock_to_cart(addr, S; zero_index = true)
```

Fock状態アドレス `addr` を直交調和振動子基底インデックス $n_x,n_y,\ldots$ に変換します。これらのインデックスは、各次元の最大状態数のタプルである `S` によって制約されます。デフォルトでは、各次元の基底状態は `0` でインデックス付けされていますが、`zero_index = false` を設定することで変更できます。
