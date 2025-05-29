```
p4est_ghost_exchange_custom_levels_end(exc)
```

非同期のゴーストデータ交換を完了します。この関数は、すべての保留中のMPI通信を待機します。

### パラメータ

  * `Data`:[in,out] [`p4est_ghost_exchange_custom_levels_begin`](@ref)によってのみ作成されます。この関数が返る前に解放されます。

### プロトタイプ

```c
void p4est_ghost_exchange_custom_levels_end (p4est_ghost_exchange_t * exc);
```
