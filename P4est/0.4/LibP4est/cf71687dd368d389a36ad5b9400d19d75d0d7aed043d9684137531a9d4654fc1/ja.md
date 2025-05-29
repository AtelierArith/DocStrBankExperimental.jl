```
p4est_connectivity_load(filename, bytes)
```

ディスクから接続構造をロードします。

### パラメータ

  * `filename`:[in] 読み込むファイルの名前。
  * `bytes`:[in,out] ディスク上の接続のサイズ（バイト）またはNULL。

### 戻り値

有効な接続を返すか、ファイルエラーの場合はNULLを返します。

### プロトタイプ

```c
p4est_connectivity_t *p4est_connectivity_load (const char *filename, size_t *bytes);
```
