```julia
struct SIHSort <: Base.Sort.Algorithm
```

補間ヒストグラムソートアルゴリズム、またはSIHSort（*sigh*ソートと発音）によるサンプリング。

# メソッド

```
SIHSort(comm)
SIHSort(comm, sorter)
SIHSort(;comm=MPI.COMM_WORLD, sorter=nothing, stats=SIHSortStats())
```

# フィールド

  * `comm::MPI.Comm`: 使用されるMPIコミュニケーター。デフォルト: MPI.COMM_WORLD
  * `root::Int64`: 削減のためのMPIルートランク。デフォルト: 0
  * `sorter::Union{Nothing, Function, Base.Sort.Algorithm}`: 使用されるローカルインプレースソーター。デフォルト: nothing
  * `stats::MPISort.SIHSortStats`: ソート後に保存される有用な統計情報、例えば要素のパーティショニング。デフォルト: SIHSortStats()
