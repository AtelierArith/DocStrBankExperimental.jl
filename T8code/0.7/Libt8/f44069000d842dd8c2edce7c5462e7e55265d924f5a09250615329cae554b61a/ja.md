```
t8_offset_range_send(start, _end, mpirank, offset_from, offset_to)
```

指定された範囲 [a,b] 内のプロセスの数をカウントし、再分配設定で特定の他のプロセスに送信します。

# 引数

  * `start`:[in] 送信者として考慮される最初の mpi ランク。
  * `end`:[in] 送信者として考慮される最後の mpi ランク。
  * `mpirank`:[in] 受信者として考慮される mpi ランク。
  * `offset_from`:[in] 現在のパーティションのパーティションテーブル。
  * `offset_to`:[in] 次のパーティションのパーティションテーブル。

# 戻り値

*start* <= p <= *end* かつ p が *mpirank* にローカルツリー（および可能性のあるゴースト）を送信するプロセスの数 p。

### プロトタイプ

```c
int t8_offset_range_send (int start, int end, int mpirank, const t8_gloidx_t *offset_from, const t8_gloidx_t *offset_to);
```
