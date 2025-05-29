```
sc_array_rewind(array, new_count)
```

配列を再割り当てせずに短縮します。

### パラメータ

  * `array`:[in,out] この配列の要素数が変更されます。
  * `new_count`:[in] **array**のカウント以下でなければなりません。もしそれが少ない場合、配列内の要素数はメモリを再割り当てせずに減少します。例外は、ビューでない配列に対して指定されたゼロの**new_count**です。この場合、sc*array*resetは同等です。

### プロトタイプ

```c
void sc_array_rewind (sc_array_t * array, size_t new_count);
```
