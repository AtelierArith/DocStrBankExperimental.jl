```
ThreadedEx(; basesize, stoppable, nestlevel, simd)
```

マルチスレッドフォールドエグゼキュータ。これは、Folds.jlおよび FLoops.jl で使用されるデフォルトの [^1] 並列エグゼキュータです。

参照: [`foldxt`](@ref), [`SequentialEx`](@ref) および [`DistributedEx`](@ref)。

[^1]: より具体的には、Folds.jl および FLoops.jl は [`PreferParallel`](@ref) を使用し、これがデフォルトで `ThreadedEx` に設定されています。

# キーワード引数

  * `basesize::Integer = amount(reducible) ÷ nthreads()`: 各ワーカーによって処理される `reducible` のチャンクのサイズ。処理する各アイテムの計算時間が大きく変動する場合や、[`reduced`](@ref) またはそれを使用するトランスデューサ（例: [`ReduceIf`](@ref)）によって計算が終了できる場合は、より小さいサイズが必要になることがあります。
  * `stoppable::Bool`: [このオプションは通常手動で設定する必要はありません。]  [`reduced`](@ref) を使用しない場合、最適化のために「停止可能」モードで実行されるスレッドフォールドにはわずかなオーバーヘッドがあります。このモードは `stoppable = false` を渡すことで無効にできます。通常は自動的に検出され、適切に設定されます。このオプションは純粋に最適化のためのものであり、結果の値には影響しません。
  * `nestlevel::Union{Integer,Val}`: いくつの内部 `Cat` (フラット化) トランスデューサをマルチスレッド化するかを指定します（[`TCat`](@ref) を使用）。正の整数、正の整数の `Val`、または `Val(:inf)` でなければなりません。`Val(:inf)` はすべての `Cat` トランスデューサに対してマルチスレッドを使用することを意味します。`Cat` トランスデューサは静的に知られている必要があります。つまり、フォールド実装は `... |> Map(f) |> Cat() |> Cat()` で二つの `Cat` を見ますが、`... |> Map(x -> f(x) |> Cat()) |> Cat()` では一つの `Cat` しか見ませんが、意味的には同じです。
  * `simd`: `true` または `:ivdep` の場合、`Base.@simd` を使用して SIMD を有効にします。`:ivdep` の場合、`@simd ivdep for ... end` バリアントを使用します。このオプションを使用するのが適切な場合を理解するには、Julia マニュアルの `Base.@simd` を参照してください。例えば、`simd = :ivdep` は、[`Scan`](@ref) のような状態を持つトランスデューサと一緒に使用してはいけません。`false`（デフォルト）の場合、`Base.@simd` は使用されません。

# 例

```jldoctest
julia> using Folds

julia> Folds.sum(1:3, ThreadedEx(basesize = 1))
6
```
