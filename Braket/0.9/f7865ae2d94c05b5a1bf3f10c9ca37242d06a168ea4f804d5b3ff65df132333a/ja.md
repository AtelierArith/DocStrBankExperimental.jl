```
simulate(d::LocalSimulator, task_specs::Vector{T}, args...; kwargs...) where {T}
```

`task_specs`で指定された*バッチ*のタスクの実行を、[`LocalSimulator](@ref) `d`のバックエンドを使用してシミュレートします。`args`はバックエンドに提供される追加の引数です。

`LocalSimulator`で使用される`kwargs`は次のとおりです：

  * `shots::Int` - `task_specs`内のすべてのタスクに対して実行するショットの数。デフォルトは`0`です。
  * `max_parallel::Int` - 同時に実行する最大シミュレーション数。デフォルトは`32`です。
  * `inputs::Union{Vector{Dict{String, Float64}}, Dict{String, Float64}}` - 各タスク仕様内の任意の[`FreeParameter`](@ref)の値を設定するために使用されます。これは`Dict`であるか、単一要素の`Vector`でなければなりません（この場合、同じパラメータ値がすべての`task_specs`の要素に使用されます）または`task_specs`と同じ長さでなければなりません（この場合、`i`番目の仕様が`i`番目の入力辞書とペアになります）。デフォルトは空の辞書です。

他の`kwargs`はバックエンドシミュレーターに渡されます。[`LocalQuantumTaskBatch`](@ref Braket.LocalQuantumTaskBatch)を返します。

!!! note
    Juliaは動的スレッディングを使用しており、`Task`はスレッド間で移動できるため、各シミュレーションは`Task`であり、それ自体がさらに多くの`Task`を生成することができます。[`LocalSimulator`](@ref)のバックエンドの内部実装は、適切な場合にスレッディングを使用する可能性があります。多くのCPUコアを持つシステムでは、あまりにも多くの`Task`を生成すると、Juliaスケジューラーが圧倒され、パフォーマンスが低下する可能性があります。「あまりにも多く」とは、ハードウェアの特性によって異なるため、多コアシステムではこの値を調整して最適なパフォーマンスを得る必要があるかもしれません。

