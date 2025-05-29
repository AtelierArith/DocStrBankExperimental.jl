```
vtk_write_array(filename, arrays, labels)
vtk_write_array(filename, array; label = "array")
```

Juliaの配列をVTK画像データファイル（.vti）に書き込みます。

配列の一般的な視覚化に便利です。入力は2Dまたは3D配列であることができます。

複数の配列はタプルとして与えることができます。例えば、

```
vtk_write_array(filename, (u, v), ("u", "v"))
```

その場合、配列は同じ次元を持っている必要があります。
