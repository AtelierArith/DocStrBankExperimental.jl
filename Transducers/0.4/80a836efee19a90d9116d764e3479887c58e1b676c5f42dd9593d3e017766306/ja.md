```
DistributedEx(; pool, basesize, threads_basesize, simd)
```

分散フォールドエグゼキュータ。Folds.jlやFLoops.jlなどのパッケージのAPIに渡して、アルゴリズムを逐次的に実行することができます。

関連情報: [`foldxd`](@ref), [`SequentialEx`](@ref) および [`ThreadedEx`](@ref)。

# キーワード引数

  * `pool::AbstractWorkerPool`: `Distributed.remotecall`に渡されます。
  * `basesize::Integer = amount(array) ÷ nworkers()`: 各ワーカーによって処理される`array`内のチャンクのサイズ。各アイテムの処理にかかる計算時間が大きく変動する場合は、より小さいサイズが必要になることがあります。
  * `threads_basesize::Integer = basesize ÷ nthreads()`: 各ワーカープロセス内の各タスクによって処理される`array`内のチャンクのサイズ。デフォルト設定では、すべてのワーカーで使用されるスレッドの数が同じであると仮定しています。各ワーカープロセスが異なるスレッド数を持つ非均質なセットアップの場合、良好なパフォーマンスを得るために、より小さい`threads_basesize` *および* `basesize`を使用する必要があるかもしれません。
  * `simd`: `true`または`:ivdep`の場合、`Base.@simd`を使用してSIMDを有効にします。`:ivdep`の場合、`@simd ivdep for ... end`のバリアントを使用します。このオプションを使用するのが適切な場合を理解するために、`Base.@simd`のJuliaマニュアルを参照してください。例えば、`simd = :ivdep`は、[`Scan`](@ref)のような状態を持つトランスデューサーと一緒に使用してはいけません。`false`（デフォルト）の場合、`Base.@simd`は使用されません。

# 例

```jldoctest
julia> using Folds

julia> Folds.sum(1:3, DistributedEx())
6
```
