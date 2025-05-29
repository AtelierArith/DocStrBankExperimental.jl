```
gaspi_proc_local_num(local_num)
```

アプリケーションによって開始されたプロセス（ランク）の数を取得します。

### パラメータ

  * `local_num`: 同じノード内のプロセス（ランク）の数

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_proc_local_num (gaspi_rank_t * const local_num);
```
