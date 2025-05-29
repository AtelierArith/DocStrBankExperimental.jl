```
p8est_ghost_exchange_data_end(exc)
```

非同期のゴーストデータ交換を完了します。この関数は、すべての保留中のMPI通信を待機します。

### パラメータ

  * `exc`:[in,out] [`p8est_ghost_exchange_data_begin`](@ref)によってのみ作成されます。この関数が戻る前に解放されます。

### プロトタイプ

```c
void p8est_ghost_exchange_data_end (p8est_ghost_exchange_t * exc);
```
