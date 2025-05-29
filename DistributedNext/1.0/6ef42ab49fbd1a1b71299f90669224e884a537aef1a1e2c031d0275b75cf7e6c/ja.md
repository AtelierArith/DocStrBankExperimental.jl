```
AbstractWorkerPool
```

ワーカープールのスーパークラスであり、[`WorkerPool`](@ref)や[`CachingPool`](@ref)などがあります。`AbstractWorkerPool`は以下を実装する必要があります：

  * [`push!`](@ref) - 新しいワーカーを全体のプールに追加する（利用可能 + ビジー）
  * [`put!`](@ref) - ワーカーを利用可能なプールに戻す
  * [`take!`](@ref) - 利用可能なプールからワーカーを取得する（リモート関数の実行に使用）
  * [`wait`](@ref) - ワーカーが利用可能になるまでブロックする
  * [`length`](@ref) - 全体のプールにおける利用可能なワーカーの数
  * [`isready`](@ref) - プールでの`take!`がブロックする場合はfalseを返し、そうでなければtrueを返す

上記のデフォルト実装（`AbstractWorkerPool`上）は、以下のフィールドを必要とします：

  * `channel::Channel{Int}`
  * `workers::Set{Int}`

ここで、`channel`は自由なワーカーピッドを含み、`workers`はこのプールに関連付けられたすべてのワーカーのセットです。
