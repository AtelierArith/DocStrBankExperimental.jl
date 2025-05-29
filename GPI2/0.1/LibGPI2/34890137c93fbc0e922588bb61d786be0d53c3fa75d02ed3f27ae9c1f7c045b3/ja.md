```
gaspi_proc_num(proc_num)
```

アプリケーションによって開始されたプロセス（ランク）の数を取得します。

### パラメータ

  * `proc_num`: アプリケーションによって開始されたプロセス（ランク）の数。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_proc_num (gaspi_rank_t * const proc_num);
```
