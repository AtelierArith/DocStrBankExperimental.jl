```
type System
```

量子システムを表す

# フィールド

  * `sites::Vector{<:AbstractSite}`: システムのサイト
  * `pure_indices::Vector{Index}`: 純粋表現のためのインデックス
  * `mixed_indices::Vector{Index}`: 混合表現のためのインデックス

# 例

```
System(10, Qubit())
System([Qubit(), SpinOne(), Qubit(), Boson(5)])
```

# インデクシング

```
system[i]          はサイト i を返す
system[Pure(), i]  は純粋インデックス i を返す
system[Mixed(), i] は混合インデックス i を返す
```
