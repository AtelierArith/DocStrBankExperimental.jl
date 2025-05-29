````
MBQCInput(indices,values)

- グラフへの入力セットを表す構造体で、空であることもできます

# パラメータ
- `indices`: 通常は整数（1からNまでの整数）のタプルで、グラフの頂点に対応します。
- `values`: タプルで、任意の型を持つことができます

# 例
```
julia> indices = (1,2,3,4)
julia> values = (0,1,1,0) #計算基底の結果
julia> mbqc_input = MBQCInput(indices,values)
```
````
