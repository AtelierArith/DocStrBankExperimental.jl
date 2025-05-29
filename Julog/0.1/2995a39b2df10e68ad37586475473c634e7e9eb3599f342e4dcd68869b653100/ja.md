```
resolve(goals, clauses; <keyword arguments>)
bwd_chain(goals, clauses; <keyword arguments>)
```

追加のPrologのような制御フローを持つ目標のSLD解決。

# 引数

  * `goals::Vector{<:Term}`: 証明またはクエリするためのJulog用語のリスト。
  * `clauses::Vector{Clause}`: Julogの節のリスト。
  * `env::Subst=Subst()`: 変数を用語にマッピングする初期環境。
  * `funcs::Dict=Dict()`: 用語を評価するためのカスタム関数。関数`f`は`funcs[:f] = f`として保存する必要があります。
  * `mode::Symbol=:all`: 結果がどのように返されるべきか。`:all`はすべての可能な置換を返します。`:any`は見つかった最初の満足する置換を返します。`:interactive`は満足する置換が見つかるたびに続行を促します。
  * `search::Symbol=:bfs`: 幅優先（`:bfs`）または深さ優先（`:dfs`）のいずれかを検索します。
  * `occurs_check::Bool=false`: 統一中の発生チェックのフラグ。
  * `defer_eval::Bool=false`: （カスタム）演算子の評価を遅延させるフラグ。
