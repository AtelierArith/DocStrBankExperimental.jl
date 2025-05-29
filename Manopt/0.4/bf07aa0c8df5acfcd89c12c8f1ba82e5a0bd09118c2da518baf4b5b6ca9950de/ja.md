```
get_cost(M::AbstractManifold,emo::EmbeddedManifoldObjective, p)
```

埋め込み内で定義された目的のコスト関数を評価します。まず、コスト関数を呼び出す前に `p` を埋め込みます。このコスト関数は [`EmbeddedManifoldObjective`](@ref) に格納されています。
