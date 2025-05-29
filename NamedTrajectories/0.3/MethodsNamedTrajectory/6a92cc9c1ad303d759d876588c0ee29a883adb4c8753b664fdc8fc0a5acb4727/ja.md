```
merge(traj1::NamedTrajectory, traj2::NamedTrajectory)
merge(trajs::AbstractVector{<:NamedTrajectory})
```

`NamedTrajectory`オブジェクトをマージすることによって新しい`NamedTrajectory`オブジェクトを返します。

マージ名は、インデックスによってマージするコンポーネントを指定するために使用されます。マージ名が提供されていない場合、すべてのコンポーネントがマージされ、名前の衝突は許可されません。マージ名が提供されている場合、名前はマージ名で提供されたインデックスのデータを使用してマージされます。

結合された`NamedTrajectory`オブジェクトは、同じタイムステップを持っている必要があります。自由時間の軌道が必要な場合、キーワード引数`free_time=true`を設定すると、タイムステップのコンポーネントが構築されます。この場合、タイムステップのシンボルを提供する必要があります。

# 引数

  * `traj1::NamedTrajectory`: 最初の`NamedTrajectory`オブジェクト。
  * `traj2::NamedTrajectory`: 2番目の`NamedTrajectory`オブジェクト。
  * `free_time::Bool=false`: 自由時間の問題を構築するかどうか。
  * `timestep_name::Symbol=:Δt`: 自由時間の問題に使用するタイムステップのシンボル。
  * `merge_names::Union{Nothing, NamedTuple{<:Any, <:Tuple{Vararg{Int}}}}=nothing`: インデックスによってマージする名前。
