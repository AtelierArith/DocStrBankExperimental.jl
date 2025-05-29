```
solve(problem, property; usecuda=false, T=Float64)
```

グラフ問題の特定のプロパティを解決します。

## 位置引数

  * `problem` はテンソネットワーク情報を持つグラフ問題です。
  * `property` はタスクを指定する文字列です。最大独立集合問題を例にすると、次のいずれかになります。

      * [`PartitionFunction`](@ref)`()` は分配関数を計算するためのものです。
      * [`SizeMax`](@ref)`(k=Single)` は最大-$k$集合サイズを見つけるためのものです。
      * [`SizeMin`](@ref)`(k=Single)` は最小-$k$集合サイズを見つけるためのものです。
      * [`CountingMax`](@ref)`(k=Single)` は最大-$k$サイズの構成を数えるためのものです。
      * [`CountingMin`](@ref)`(k=Single)` は最小-$k$サイズの構成を数えるためのものです。
      * [`CountingAll`](@ref)`()` はすべての構成を数えるためのものです。
      * [`PartitionFunction`](@ref)`()` はすべての構成を数えるためのものです。
      * [`GraphPolynomial`](@ref)`(; method=:finitefield, kwargs...)` はグラフ多項式を評価するためのものです。
      * [`SingleConfigMax`](@ref)`(k=Single; bounded=false)` は各サイズの最大-$k$構成を1つ見つけるためのものです。
      * [`SingleConfigMin`](@ref)`(k=Single; bounded=false)` は各サイズの最小-$k$構成を1つ見つけるためのものです。
      * [`ConfigsMax`](@ref)`(k=Single; bounded=true, tree_storage=false)` は最大-$k$サイズの構成を列挙するためのものです。
      * [`ConfigsMin`](@ref)`(k=Single; bounded=true, tree_storage=false)` は最小-$k$サイズの構成を列挙するためのものです。
      * [`ConfigsAll`](@ref)`(; tree_storage=false)` はすべての構成を列挙するためのものです。

## キーワード引数

  * `usecuda` はCUDAを使用するためのスイッチです（可能な場合）。このスイッチをオンにする前に、ユーザーは `using CUDA` ステートメントを呼び出す必要があります。
  * `T` は「ベース」要素タイプであり、時にはメモリコストを削減するために使用できます。
