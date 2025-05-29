```
gaspi_print_error(error_code, error_message)
```

エラーコードをテキストメッセージに変換します。注意：パラメータ error_message はメモリを割り当てるため、アプリケーションはそれを解放する必要があります（free()を使用）。

### パラメータ

  * `error_code`: 変換するエラーコード。
  * `error_message`: テキストメッセージを含む出力パラメータ。

### 戻り値

成功の場合は GASPI*SUCCESS、error*message バッファの割り当てにエラーがあった場合は GASPI*ERR*MEMALLOC を返します。

### プロトタイプ

```c
gaspi_return_t gaspi_print_error( gaspi_return_t error_code, gaspi_string_t *error_message);
```
