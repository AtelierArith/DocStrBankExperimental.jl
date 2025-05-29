```
add_format(fmt, magic, extension)
```

は新しい [`DataFormat`](@ref) を登録します。

例えば：

```julia
add_format(format"TIFF", (UInt8[0x4d,0x4d,0x00,0x2b], UInt8[0x49,0x49,0x2a,0x00]), [".tiff", ".tif"])
add_format(format"PNG", [0x89,0x50,0x4e,0x47,0x0d,0x0a,0x1a,0x0a], ".png")
add_format(format"NRRD", "NRRD", [".nrrd",".nhdr"])
```

拡張子、マジックナンバー、およびフォーマット識別子は大文字と小文字を区別します。

`add_format(fmt, magic, extension, pkgspecifiers...)` を使用して、フォーマットをサポートする特定のパッケージを指定することもできます。例としての `pkgspecifiers` は次の通りです：

```julia
add_format(fmt, magic, extension, [:PkgA=>UUID(...)])                     # PkgA のみがフォーマットをサポートします（読み込みと保存）
add_format(fmt, magic, extension, [:PkgA=>uuidA], [:PkgB=>uuidB])         # まず PkgA を試し、失敗した場合は PkgB を試します
add_format(fmt, magic, extension, [:PkgA=>uuidA, LOAD], [:PkgB=>uuidB])   # `load` のためにまず PkgA を試し、そうでなければ PkgB を使用します
add_format(fmt, magic, extension, [:PkgA=>uuidA, OSX], [:PkgB=>uuidB])    # OSX では PkgA を使用し、それ以外では PkgB を使用します
```

`uuid` はすべて `UUID` 型であり、パッケージの `Project.toml` ファイルから取得できます。

`LOAD`、`SAVE`、`OSX`、`Unix`、`Windows`、および `Linux` を任意に組み合わせて `pkgspecifiers` を絞り込むことができます。
