```
p4est_memory_used(p4est_)
```

フォレスト構造のローカルメモリ使用量を計算します。集団的ではありません。現在のランクで使用されているメモリが返されます。接続構造は所有されていないためカウントされません。`p4est_connectivity_memory_usage`（`p4est`->connectivity）を使用してください。

### パラメータ

  * `p4est`:[in] 有効なフォレスト構造。

### 戻り値

バイト単位で使用されているメモリ。

### プロトタイプ

```c
size_t p4est_memory_used (p4est_t * p4est);
```
