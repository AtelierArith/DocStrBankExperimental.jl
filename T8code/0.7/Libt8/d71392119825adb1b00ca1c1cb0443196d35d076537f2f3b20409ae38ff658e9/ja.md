```
t8_offset_sendsto(proca, procb, t8_offset_from, t8_offset_to)
```

再分配設定において、特定のプロセスが別のプロセスにローカルツリー（およびその後にゴーストがある場合）を送信するかどうかを照会します。

# 引数

  * `proca`:[in] 送信可能なプロセスのMpiランク。
  * `procb`:[in] 受信可能なプロセスのMpiランク。
  * `offset_from`:[in] 現在のパーティションのパーティションテーブル。
  * `offset_to`:[in] 次のパーティションのパーティションテーブル。

# 戻り値

*proca*が*offset_from*から*offset_to*に再分配する際に*procb*にローカルツリーを送信する場合は非ゼロ、そうでない場合は0。

### プロトタイプ

```c
int t8_offset_sendsto (int proca, int procb, const t8_gloidx_t *t8_offset_from, const t8_gloidx_t *t8_offset_to);
```
