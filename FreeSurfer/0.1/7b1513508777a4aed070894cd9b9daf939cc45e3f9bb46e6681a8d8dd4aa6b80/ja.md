```
mri_read_bfiles(infile1::String, infile2::String)
```

テキストファイル `infile1` と `infile2` からDWI b値テーブルと勾配テーブルを読み込みます。2つの入力ファイルは任意の順序で指定できます。勾配テーブルファイルは、b値テーブルファイルの3倍のエントリを含む必要があります。

b値テーブルをサイズnのベクトルとして、勾配テーブルをサイズ(n, 3)の行列として返します。
