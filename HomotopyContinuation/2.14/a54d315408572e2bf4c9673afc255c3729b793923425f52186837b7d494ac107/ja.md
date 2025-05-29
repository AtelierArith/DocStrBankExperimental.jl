```
UniquePoints{T, Id, M}
```

与えられた距離関数 `M` によって決定されたインデックス付きポイントに対して、ポイントが近いかどうかを迅速に評価するためのデータ構造です。インデックス付きポイントは、その識別子 `Id` のみで保存されます。距離関数が三角不等式を満たす場合は `triangle_inequality` を `true` に設定する必要があります。そうでない場合は `false` に設定します。`triangle_inequality` が何も指定されていない場合、アルゴリズムは三角不等式が満たされているかどうかを検出しようとします。

```
UniquePoints(v::AbstractVector{T}, id::Id;
                distance = EuclideanNorm(),
                triangle_inequality = nothing,
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
