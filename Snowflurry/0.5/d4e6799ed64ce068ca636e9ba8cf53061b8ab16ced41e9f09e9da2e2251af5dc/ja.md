```
LineConnectivity <:AbstractConnectivity
```

任意子系のQPUの線形キュービット接続性を記述するデータ構造。この接続タイプは、[`AnyonYukonQPU`](@ref)のような`QPUs`で遭遇します。

# フィールド

  * `dimension         ::Int` – この接続性のためのキュービットの数。
  * `excluded_positions::Vector{Int}` – オプション: 接続性上で無効化され、操作を実行できないキュービットのリスト。`Vector`の要素は一意でなければなりません。
  * `excluded_connections::Vector{Tuple{Int, Int}}` – オプション: 無効化され、2キュービットゲートを実行できないキュービット間の接続のリスト。`Vector`の要素は一意でなければなりません。各接続はキュービットインデックスの`Tuple`として提供されます。

!!! note
    すべての除外接続は昇順にソートされています（つまり、接続(2, 1)は(1, 2)に変更されます）。


# 例

```jldoctest
julia> connectivity = LineConnectivity(6)
LineConnectivity{6}
1──2──3──4──5──6

julia> connectivity = LineConnectivity(6, [1,2,3], [(3, 2), (3, 4)])
LineConnectivity{6}
1──2──3──4──5──6
excluded positions: [1, 2, 3]
excluded connections: [(2, 3), (3, 4)]

```
