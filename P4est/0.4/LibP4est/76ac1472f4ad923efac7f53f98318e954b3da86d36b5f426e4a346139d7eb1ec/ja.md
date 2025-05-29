```
p8est_save_ext(filename, p8est_, save_data, save_partition)
```

完全な接続性/`p8est`データをディスクに保存します。これは、すべてのMPIプロセスが呼び出す必要がある集団操作です。すべてのプロセスが同じファイルに書き込むため、指定されたファイル名はすべての並列呼び出しで同一である必要があります。自動パーティションパラメータに関する情報は[`p8est_load_ext`](@ref)を参照してください。

!!! note
    ファイルエラーで中止します。


### パラメータ

  * `filename`:[in] 書き込むファイルの名前。
  * `p8est`:[in] 有効なフォレスト構造。
  * `save_data`:[in] trueの場合、要素データが保存されます。そうでない場合、データサイズは0が保存されます。
  * `save_partition`:[in] falseの場合、1コアを使用しているかのようにファイルを保存します。trueの場合、コア数とパーティションを保存します。利点：同じmpisizeと自動パーティションがfalseのときに、パーティションを読み込むことができます。欠点：ファイルがmpisizeに依存するようになります。いずれにせよ、ファイルは自動パーティションがtrueの状態で読み込むことができます。

### プロトタイプ

```c
void p8est_save_ext (const char *filename, p8est_t * p8est, int save_data, int save_partition);
```
