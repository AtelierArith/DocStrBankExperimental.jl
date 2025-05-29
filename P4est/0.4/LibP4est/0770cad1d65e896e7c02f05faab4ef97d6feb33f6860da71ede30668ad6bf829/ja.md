```
p6est_save(filename, p6est_, save_data)
```

完全な接続性/`p6est`データをディスクに保存します。これは全てのMPIプロセスが呼び出す必要がある集団操作です。全てのプロセスが同じファイルに書き込むため、指定されたファイル名は全ての並列呼び出しで同一である必要があります。

!!! note
    ファイルエラーで中止します。


### パラメータ

  * `filename`:[in] 書き込むファイルの名前。
  * `p6est`:[in] 有効なフォレスト構造。
  * `save_data`:[in] trueの場合、要素データが保存されます。そうでない場合、データサイズは0が保存されます。

### プロトタイプ

```c
void p6est_save (const char *filename, p6est_t * p6est, int save_data);
```
