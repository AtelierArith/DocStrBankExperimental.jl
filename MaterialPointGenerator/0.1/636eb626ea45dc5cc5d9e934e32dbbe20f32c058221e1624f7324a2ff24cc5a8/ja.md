```
polygon2particle(stl_file, output_file, h; verbose=true)
```

## 説明:

指定された `.stl` ファイルから構造化された粒子を生成します。粒子は STL モデルの 2D 空間をボクセル化することによって生成されます。ボクセルサイズ `h` は正である必要があります。
