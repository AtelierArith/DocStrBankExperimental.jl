```
t8_offset_sendstree(proc_send, proc_to, gtree, offset_from, offset_to)
```

再分配設定において、特定のプロセスが特定のツリーを別のプロセスに送信するかどうかを照会します。

# 引数

  * `proc_send`:[in] 送信可能なプロセスのMpiランク。
  * `proc_recv`:[in] 受信可能なプロセスのMpiランク。
  * `gtree`:[in] グローバルツリーID。
  * `offset_from`:[in] 現在のパーティションのパーティションテーブル。
  * `offset_to`:[in] 次のパーティションのパーティションテーブル。

# 戻り値

*proc_send* が *proc_recv* にツリー *gtree* を送信する場合は非ゼロ、そうでない場合は0を返します。呼び出す際、*gtree* は *offset_from* の *proc_send* のローカルツリーであってはなりません。この場合、常に0が返されます。

### プロトタイプ

```c
int t8_offset_sendstree (int proc_send, int proc_to, t8_gloidx_t gtree, const t8_gloidx_t *offset_from, const t8_gloidx_t *offset_to);
```
