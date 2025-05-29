```
sc_vtk_write_binary(vtkfile, numeric_data, byte_length)
```

この関数は、VTKのbase64エンコーディングで数値のバイナリデータを書き込みます。

### パラメータ

  * `vtkfile`: 書き込み用に開かれたストリーム。
  * `numeric_data`: 数値データ配列へのポインタ。
  * `byte_length`: バイト単位のデータ配列の長さ。

### 戻り値

成功時は0を返し、ファイルエラー時は-1を返します。

### プロトタイプ

```c
int sc_vtk_write_binary (FILE * vtkfile, char *numeric_data, size_t byte_length);
```
