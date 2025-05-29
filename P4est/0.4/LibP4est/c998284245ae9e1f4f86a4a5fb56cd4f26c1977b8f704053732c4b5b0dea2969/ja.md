```
p4est_connectivity_save(filename, connectivity)
```

接続構造をディスクに保存します。

### パラメータ

  * `filename`:[in] 書き込むファイルの名前。
  * `connectivity`:[in] 有効な接続構造。

### 戻り値

成功した場合は0を返し、ファイルエラーの場合は非ゼロを返します。

### プロトタイプ

```c
int p4est_connectivity_save (const char *filename, p4est_connectivity_t * connectivity);
```
