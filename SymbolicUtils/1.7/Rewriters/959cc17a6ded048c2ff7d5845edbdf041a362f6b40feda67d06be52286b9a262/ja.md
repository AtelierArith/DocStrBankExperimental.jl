リライターは、式を受け取り、式または `nothing` を返す任意の関数です。`nothing` が返される場合、それは入力式に適用可能な変更がなかったことを意味します。

`Rewriters` モジュールには、リライターを作成および変換するいくつかの型が含まれています。

  * `Empty()` は常に `nothing` を返すリライターです。
  * `Chain(itr)` はリライターのイテレータを単一のリライターに連結し、指定された順序で各連結リライターを適用します。リライターが `nothing` を返す場合、これは変更なしとして扱われます。
  * `RestartedChain(itr)` は `Chain(itr)` と同様ですが、連結リライターのいずれかが最初に成功した適用を行った後、最初のリライターから再スタートします。
  * `IfElse(cond, rw1, rw2)` は入力に対して `cond` 関数を実行し、`cond` が true を返す場合は `rw1` を適用し、false を返す場合は `rw2` を適用します。
  * `If(cond, rw)` は `IfElse(cond, rw, Empty())` と同じです。
  * `Prewalk(rw; threaded=false, thread_cutoff=100)` は、指定された式の前順走査を行い、リライター `rw` を適用するリライターを返します。`rw` が一致が見つからない場合に `nothing` を返すと、`Prewalk(rw)` も一致が見つかるまで `nothing` を返します。`threaded=true` は走査にマルチスレッドを使用します。`thread_cutoff` は、スレッド化されたスパウンで走査されるべきサブツリー内のノードの最小数です。
  * `Postwalk(rw; threaded=false, thread_cutoff=100)` は、同様に後順走査を行います。
  * `Fixpoint(rw)` は、変更がなくなるまで `rw` を繰り返し適用するリライターを返します。
  * `FixpointNoCycle` は [`Fixpoint`](@ref) のように動作しますが、代わりに新しい結果を返している間のみ `rw` を繰り返し適用します。
  * `PassThrough(rw)` は、`rw(x)` が `nothing` を返す場合は `x` を返し、それ以外の場合は `rw(x)` を返すリライターを返します。
