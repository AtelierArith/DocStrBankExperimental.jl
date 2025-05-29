```
PlaybackPolicy{A<:AbstractArray, P<:Policy, V<:AbstractArray{<:Real}}
```

すべてのアクションが使用されるまで固定されたアクションのシーケンスを適用し、その後エピソードの終わりまでバックアップポリシーにフォールバックするポリシーです。

コンストラクタ:

```
`PlaybackPolicy(actions::AbstractArray, backup_policy::Policy; logpdfs::AbstractArray{Float64, 1} = Float64[])`
```

# フィールド

  * `actions::Vector{A}` 再生するアクションのベクター
  * `backup_policy::Policy` 指定されたすべてのアクションが取られたときに使用するポリシーですが、エピソードは続きます
  * `logpdfs::Vector{Float64}` アクションの対数確率（密度）
  * `i::Int64` 現在のアクションインデックス
