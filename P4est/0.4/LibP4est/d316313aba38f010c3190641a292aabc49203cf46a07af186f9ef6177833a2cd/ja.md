```
p8est_save(filename, p8est_, save_data)
```

完全な接続性/`p8est`データをディスクに保存します。

これは全てのMPIプロセスが呼び出す必要がある集団操作です。全てのプロセスが同じファイルに書き込むため、指定されたファイル名は全ての並列呼び出しで同一である必要があります。

デフォルトでは、現在のプロセッサ数とパーティションをファイルヘッダーに書き込みます。これにより、ファイルはmpisizeに依存します。これを変更するには、`p8est_save_ext`(@ref)()をp8est_extended.hで参照してください。

リビジョンカウンタはファイルに保存されません。なぜなら、異なるリビジョンから来たファイルが同じメッシュを保存している場合、ファイルが異なることになるからです。

!!! note
    ファイルエラーが発生した場合は中止します。


!!! note
    `p4est`がMPI-IOを使用するように設定されていない場合、一部のプロセスはファイルが完全になる前にこの関数から戻るため、その場合、ファイルへの即時読み取りアクセスには`sc_MPI_Barrier`の呼び出しが必要になることがあります。


### パラメータ

  * `filename`:[in] 書き込むファイルの名前。
  * `p8est`:[in] 有効なフォレスト構造。
  * `save_data`:[in] trueの場合、要素データが保存されます。そうでない場合、データサイズは0が保存されます。

### プロトタイプ

```c
void p8est_save (const char *filename, p8est_t * p8est, int save_data);
```
