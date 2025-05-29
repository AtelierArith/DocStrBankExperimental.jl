```
sc_fwrite(ptr, size, nmemb, file, errmsg)
```

メモリの内容をファイルに書き込みます。

!!! note
    この関数はファイルエラーが発生した場合に中止します。


### パラメータ

  * `ptr`:[in] ディスクに書き込むデータ配列。
  * `size`:[in] 一つの配列メンバーのサイズ。
  * `nmemb`:[in] 配列メンバーの数。
  * `file`:[in,out] 書き込み用に開かれている必要があるファイルポインタ。
  * `errmsg`:[in] `SC_CHECK_ABORT`に渡されるエラーメッセージ。

### プロトタイプ

```c
void sc_fwrite (const void *ptr, size_t size, size_t nmemb, FILE * file, const char *errmsg);
```
