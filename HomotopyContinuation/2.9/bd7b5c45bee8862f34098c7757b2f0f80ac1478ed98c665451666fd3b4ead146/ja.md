```
UniquePoints{T, Id, M}
```

与えられた距離関数 `M` によって決定されたインデックス付きポイントに対して、ポイントが近いかどうかを迅速に評価するためのデータ構造です。距離関数は *メトリック* でなければなりません。インデックス付きポイントは、その識別子 `Id` のみで保存されます。

```
UniquePoints(v::AbstractVector{T}, id::Id;
                metric = EuclideanNorm(),
                group_actions = nothing)
```

データ構造を初期化します。この *初期化* はポイントでデータ構造を初期化するものではありません。

## 例

```julia
x = randn(ComplexF64, 4)
permutation(x) = ([x[2]; x[1]; x[3]; x[4]],)
group_actions = GroupActions(permutation)
X = group_actions(x)

# グループアクションなし
unique_points = UniquePoints(x, 1)
HC.add!.(unique_points, X, 1:length(X), 1e-5)
length(unique_points) # 2

unique_points = UniquePoints(x, 1, group_actions = group_actions)
HC.add!.(unique_points, X, 1:length(X), 1e-5)
length(unique_points) # 1
```
