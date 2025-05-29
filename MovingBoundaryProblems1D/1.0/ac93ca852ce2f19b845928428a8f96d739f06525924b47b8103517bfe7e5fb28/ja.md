```
MBGeometry{T}
```

移動境界問題の幾何学の定義。

# フィールド

  * `mesh_points::T`: メッシュポイント。ソートされている必要があり、`mesh_points[begin] = 0` および `mesh_points[end] = 1` を満たす必要があります（これを満たさない場合は、最初にスケーリングされます）。
  * `spacings::T`: メッシュポイント間の間隔。
  * `volumes::T`: メッシュポイントによって定義されたセルの体積。

# コンストラクタ

幾何学を構築するには、デフォルトコンストラクタを直接呼び出すことができます。

```
MBGeometry(mesh_points, spacings, volumes)
```

または、便利なコンストラクタを呼び出すことができます。

```
MBGeometry(mesh_points)
```

これにより、間隔と体積が自動的に計算されます。

[`MBProblem`](@ref) も参照してください。
