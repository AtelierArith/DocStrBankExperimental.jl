```
extract_paths(tree::PositionTree{N,T})
```

PositionTreeからすべての根から葉へのパスを抽出します。

# 引数

  * `tree::PositionTree{N,T}`: PositionTreeの根。

# 戻り値

  * 各パスが根から葉までの位置のベクトル（SVectorsとして）であるパスの配列。

# 例

```julia
root = PositionTree([1.0, 2.0, 3.0])
push!(root.subpoints, PositionTree([4.0, 5.0, 6.0]))
push!(root.subpoints, PositionTree([7.0, 8.0, 9.0]))

paths = extract_paths(root)
```
