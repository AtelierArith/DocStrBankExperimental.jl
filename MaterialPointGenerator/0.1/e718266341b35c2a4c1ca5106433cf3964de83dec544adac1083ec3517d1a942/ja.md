```
polygon2particle(stl_file, msh_file, output_file, nid_file, h; verbose=true)
```

## 説明:

与えられた `.stl` ファイルと `.msh` ファイルから構造化された粒子を生成します。粒子はSTLモデルの2D空間をボクセル化することによって生成されます。ボクセルサイズ `h` は正である必要があります。
