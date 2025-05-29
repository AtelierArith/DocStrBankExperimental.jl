```
p8est_ghost_exchange_custom_end(exc)
```

非同期のゴーストデータ交換を完了します。この関数は、すべての保留中のMPI通信を待機します。

### パラメータ

  * `Data`:[in,out] [`p8est_ghost_exchange_custom_begin`](@ref)によってのみ作成されます。この関数が返る前に解放されます。

### プロトタイプ

```c
void p8est_ghost_exchange_custom_end (p8est_ghost_exchange_t * exc);
```
