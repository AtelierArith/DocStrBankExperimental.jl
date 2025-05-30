```
GroupedArray(args... [; coalesce = false, sort = true])
```

`args`の要素によって形成されたグループの異なる値を持つ`GroupedArray`を構築します。

### 引数

  * `args...`: 同じサイズの`AbstractArrays`。

### キーワード引数

  * `coalesce::Bool`: 欠損値を異なるグループの指標として考慮すべきか？
  * `sort::Union{Bool, Nothing}`: グループの順序をソート順にすべきか？最良のパフォーマンスのために`nothing`に設定します。

### 例

```julia
using GroupedArrays
p1 = ["a", "a", "b", "b", missing, missing]
GroupedArray(p1)
GroupedArray(p1; coalesce = true)
p2 = [1, 1, 1, 2, 2, 2]
GroupedArray(p1, p2)
```
