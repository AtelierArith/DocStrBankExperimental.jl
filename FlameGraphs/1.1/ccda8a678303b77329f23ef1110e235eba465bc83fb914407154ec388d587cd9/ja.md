```
g = flamegraph(data=Profile.fetch(); lidict=nothing, C=false, combine=true, recur=:off, norepl=true, pruned=[], filter=nothing)
```

プロファイリングデータを表すグラフを計算します。現在収集されたプロファイリング情報のために計算する場合は、`data`と`lidict`の両方を省略してください。保存されたプロファイリングデータのために計算する場合は、両方を指定してください。(`data`と`lidict`は`Profile.retrieve()`からの一致したペアでなければなりません。)

以下のキーワードで戦略を制御できます：

  * `C`: `true`の場合、`ccall`されたコードから収集されたスタックフレームを含めます。
  * `recur` (Julia 1.4+でサポート): 再帰呼び出しを反復に対応するかのように表現します。
  * `norepl`: `true`の場合、`REPL.eval_user_input`より深いスタックトレースの部分は破棄されます。
  * `pruned`: このフレームグラフの枝を終了させるトリガーとなる`(funcname, filename)`ペアのリストです。これを使用して、非常に「高い」グラフを深い再帰呼び出しから防ぐことができます。例えば、`pruned = [("sort!", "sort.jl")]`は、Juliaの`sort!`関数に対応するノードとそれによって呼び出されるものを省略します。代替戦略については`recur`も参照してください。
  * `combine`: `true`の場合、同じコード行に対応する命令ポインタが単一のスタックフレームに結合されます。
  * `filter`: フィルター条件を満たさないすべての枝を削除します。`Condition`は`string`、`regex`、または`NodeData`に適用できる任意の関数です。例えば、`filter = "mapslices"`または同等に`filter = x -> (x.sf.func == :mapslices)`は、`mapslices`ノードを子または祖先として含まないすべての枝を削除します。
  * `threads::Union{Int,AbstractVector{Int},Nothing}`: サンプルを含めるスレッドを指定します。`nothing`はすべてを返します。
  * `tasks::Union{Int,AbstractVector{Int},Nothing}`: サンプルを含めるタスクを指定します。`nothing`はすべてを返します。

!!! compat 1.8     `threads`および`tasks`のキーワード引数はjulia 1.8を必要とします。

`g`は[`AbstractTrees.jl`の](https://github.com/JuliaCollections/AbstractTrees.jl) `print_tree`を使用して検査できます。
