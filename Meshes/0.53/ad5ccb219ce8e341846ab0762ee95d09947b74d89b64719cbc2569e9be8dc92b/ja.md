```
Shadow(dims)
```

与えられた `dims` にジオメトリまたはドメインを投影し、元のオブジェクトの「影」を生成します。

## 例

```julia
Shadow(:xy)
Shadow("xz")
Shadow(1, 2)
Shadow((1, 3))
```
