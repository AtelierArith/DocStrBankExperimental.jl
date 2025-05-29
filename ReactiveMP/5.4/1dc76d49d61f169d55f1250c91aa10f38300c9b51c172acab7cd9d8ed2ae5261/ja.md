```
marginalrule(fform, on, mnames, messages, qnames, marginals, meta, __node)
```

この関数は、指定されたノードのローカルな結合周辺を計算するために使用されます。

# 引数

  * `fform`: ノードの機能形式、ノードの型の形式で、例えば `::Type{ <: NormalMeanVariance }` または `::typeof(+)`
  * `on`: ローカルな結合周辺タグ、例えば `::Val{ :mean_precision }` または `::Val{ :out_mean_precision }`
  * `mnames`: Val型の形式での順序付けされたメッセージ名、例えば `::Val{ (:mean, :precision) }`
  * `messages`: アウトバウンドメッセージを計算するために使用される `mnames` と同じ長さのメッセージのタプル
  * `qnames`: Val型の形式での順序付けされた周辺名、例えば `::Val{ (:mean, :precision) }`
  * `marginals`: アウトバウンドメッセージを計算するために使用される `qnames` と同じ長さの周辺のタプル
  * `meta`: 追加のメタ情報
  * `__node`: ノード参照

参照: [`rule`](@ref), [`@rule`](@ref) [`@marginalrule`](@ref)
