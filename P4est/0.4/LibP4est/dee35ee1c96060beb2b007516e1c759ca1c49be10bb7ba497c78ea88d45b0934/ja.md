```
sc_fread(ptr, size, nmemb, file, errmsg)
```

ファイルの内容をメモリに読み込みます。

!!! note
    この関数はファイルエラーが発生した場合に中止します。


### パラメータ

  * `ptr`:[out] ディスクから読み込むデータ配列。
  * `size`:[in] 配列の1つのメンバーのサイズ。
  * `nmemb`:[in] 配列メンバーの数。
  * `file`:[in,out] ファイルポインタ、読み取り用に開かれている必要があります。
  * `errmsg`:[in] `SC_CHECK_ABORT`に渡されるエラーメッセージ。

### プロトタイプ

```c
void sc_fread (void *ptr, size_t size, size_t nmemb, FILE * file, const char *errmsg);
```
