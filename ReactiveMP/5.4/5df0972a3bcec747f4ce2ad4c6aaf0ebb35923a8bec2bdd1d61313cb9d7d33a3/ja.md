```
rule(fform, on, vconstraint, mnames, messages, qnames, marginals, meta, __node)
```

この関数は、特定のノードに対するアウトバウンドメッセージを計算するために使用されます。

# 引数

  * `fform`: ノードの機能的形式、ノードの型の形式で、例えば `::Type{ <: NormalMeanVariance }` または `::typeof(+)`
  * `on`: メッセージを計算する必要があるアウトバウンドインターフェースのタグ、例えば `::Val{:out}` または `::Val{:μ}`
  * `vconstraint`: アウトバウンドインターフェースの変数制約、例えば `Marginalisation` または `MomentMatching`
  * `mnames`: Val型の形式での順序付けされたメッセージ名、例えば `::Val{ (:mean, :precision) }`
  * `messages`: アウトバウンドメッセージを計算するために使用される `mnames` と同じ長さのメッセージのタプル
  * `qnames`: Val型の形式での順序付けされた周辺名、例えば `::Val{ (:mean, :precision) }`
  * `marginals`: アウトバウンドメッセージを計算するために使用される `qnames` と同じ長さの周辺のタプル
  * `meta`: 追加のメタ情報
  * `addons`: 追加のアドオン情報
  * `__node`: ノード参照

利用可能なすべてのルールについては、`ReactiveMP.print_rules_table()`を参照してください。

関連情報: [`@rule`](@ref), [`marginalrule`](@ref), [`@marginalrule`](@ref)
