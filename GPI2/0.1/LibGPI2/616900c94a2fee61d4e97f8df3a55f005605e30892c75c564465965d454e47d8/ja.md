```
gaspi_segment_avail_local(avail_seg_id)
```

ローカルで利用可能なセグメントIDを取得します。

セグメントを作成/割り当てるには、アプリケーションがセグメントIDを提供する必要があります。これは、呼び出しランクのローカルで次の利用可能なIDを見つけるためのヘルパー関数を提供します。

### パラメータ

  * `avail_seg_id`: 利用可能なセグメントID。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_segment_avail_local (gaspi_segment_id_t* const avail_seg_id);
```
