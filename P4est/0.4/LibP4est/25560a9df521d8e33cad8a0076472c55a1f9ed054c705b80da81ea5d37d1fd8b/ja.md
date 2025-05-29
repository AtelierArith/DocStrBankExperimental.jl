```
sc_fflush_fsync_fclose(file)
```

ディスクにファイルのデータをフラッシュし、閉じるための最善の努力。

### パラメータ

  * `file`:[in,out] 書き込みのためにオープンされたファイル。

### プロトタイプ

```c
void sc_fflush_fsync_fclose (FILE * file);
```
