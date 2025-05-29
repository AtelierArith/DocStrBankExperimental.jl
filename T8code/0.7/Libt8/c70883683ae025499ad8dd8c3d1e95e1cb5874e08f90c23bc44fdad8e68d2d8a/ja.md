```
t8_cmesh_vtk_write_file(cmesh, fileprefix)
```

cmeshを.pvtuファイル形式で書き込みます。プロセスごとに1つの.vtuファイルとメタ.pvtuファイルを書き込みます。この関数はASCIIファイルを書き込み、t8codeが「–with-vtk」で構成されていない場合やt8*cmesh*vtk*write*file*via*APIが利用できない場合に使用できます。

# 引数

  * `cmesh`:[in] cmesh
  * `fileprefix`:[in] 出力ファイルのプレフィックス

# 戻り値

int

### プロトタイプ

```c
int t8_cmesh_vtk_write_file (t8_cmesh_t cmesh, const char *fileprefix);
```
