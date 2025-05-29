```
make_bim_fam_files(x::SnpArray, y, name::String)
```

SnpArrayから.bimおよび.bedファイルを作成します。

# 引数:

  * `x`: 対応する.bimおよび.famファイルを作成したいSnpArray（すなわち、ディスク上の.bedファイル）。
  * `name`: .bedファイルと一致する文字列（`name`に.bimまたは.fam拡張子を含めないでください）。
  * `y`: .famファイルの6列目に入る特性ベクトル。
