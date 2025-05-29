# FLoops: `fold` for humans™

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliafolds2.github.io/FLoops.jl/dev) [![GitHub Actions](https://github.com/JuliaFolds2/FLoops.jl/workflows/Run%20tests/badge.svg)](https://github.com/JuliaFolds/FLoops.jl/actions?query=workflow%3A%22Run+tests%22)

[FLoops.jl](https://github.com/JuliaFolds2/FLoops.jl) はマクロ `@floop` を提供します。これは、複雑なコレクションに対して高速な汎用の逐次および並列イテレーションを生成するために使用できます。

さらに、`@floop` で書かれたループは、互換性のある任意の[エグゼキュータ](@ref tutorials-executor)で実行できます。さまざまなスレッドベースのエグゼキュータについては、[FoldsThreads.jl](https://github.com/JuliaFolds2/FoldsThreads.jl)を参照してください。これらは異なる種類のループに最適化されています。[FoldsCUDA.jl](https://github.com/JuliaFolds/FoldsCUDA.jl)はGPU用のエグゼキュータを提供します。FLoops.jlは、シンプルな分散エグゼキュータも提供します。

## 更新ノート

FLoops.jl 0.2はデフォルトで並列ループを使用します。つまり、エグゼキュータが指定されておらず、明示的な逐次形式 `@floop begin ... end` が使用されていない場合、並列エグゼキュータ（例：`ThreadedEx`）を使用します。

つまり、`@reduce`なしの `@floop` は次のようになります。

```JULIA
@floop for i in eachindex(ys, xs)
    ys[i] = f(xs[i])
end
```

これはデフォルトで並列に実行されます。

## 使用法

### 並列ループ

`@floop` は `Threads.@threads` のスーパーセットであり、特に追加の構文 `@reduce` を使用して複雑な還元をサポートします：

```jldoctest README
julia> using FLoops  # @floop マクロをエクスポート

julia> @floop for (x, y) in zip(1:3, 1:2:6)
           a = x + y
           b = x - y
           @reduce s += a
           @reduce t += b
       end
       (s, t)
(15, -3)
```

詳細な例については、[並列ループのチュートリアル](@ref tutorials-parallel)を参照してください。

### 逐次（シングルスレッド）ループ

`for` ループとその初期化部分を `@floop begin ... end` でラップするだけです：

```jldoctest README
julia> @floop begin
           s = 0
           for x in 1:3
               s += x
           end
       end
       s
6
```

詳細な例については、[逐次ループのチュートリアル](@ref tutorials-sequential)を参照してください。

## `Threads.@threads` に対する利点

`@floop` は `Threads.@threads` のスーパーセットであり、いくつかの利点があります：

  * `@floop` は配列、辞書、セット、文字列、`zip` や `product` などの `Base.Iterators` からの多くのイテレータを含むさまざまな入力コレクションタイプをサポートします。より正確には、`@floop` は [SplittablesBase.jl](https://github.com/JuliaFolds2/SplittablesBase.jl) インターフェースをサポートする任意のコレクションに対して高性能な並列イテレーションを生成できます。
  * [`FoldsThreads.NondeterministicEx`](https://juliafolds2.github.io/FoldsThreads.jl/dev/#FoldsThreads.NondeterministicEx) を使用すると、`@floop` は非並列化可能な入力コレクションに対するイテレーションを並列化することさえできます（ただし、これは重い作業負荷に対してのみ有益です）。
  * [FoldsThreads.jl](https://github.com/JuliaFolds2/FoldsThreads.jl) は、ループ自体に触れることなくパフォーマンスを調整するために使用できる複数の代替スレッドベースのエグゼキュータ（= ループ実行バックエンド）を提供します。
  * [FoldsCUDA.jl](https://github.com/JuliaFolds/FoldsCUDA.jl) はシンプルなGPUエグゼキュータを提供します。
  * 複雑な還元を前方互換性のある方法でサポートするための `@reduce` 構文

      * 注：`@threads` と組み合わせて一般的に使用される `threadid` ベースの還元は、スレッド間でタスクを移行することをサポートするJuliaに対して前方互換性がない場合があります。
  * [`julia` を再起動せずに `basesize` オプションを使用してスレッドの実効数を「変更する」ためのトリックがあります](https://juliafolds2.github.io/data-parallelism/howto/faq/#set-nthreads-at-run-time)。

相対的な欠点は、`@floop` が `Threads.@threads` よりもはるかに新しく、内部がはるかに柔軟であることです。これらの点は、未発見のバグに寄与する可能性があります。

## 仕組み

`@floop` は、ネイティブのJulia `for` ループ構文を [Transducers.jl](https://github.com/JuliaFolds2/Transducers.jl) によって定義された `foldl` に変換することによって機能します。`Base` で定義された `foldl` とは異なり、Transducers.jl で定義された `foldl` は [`for` ループのセマンティクスとそれ以上をカバーするのに十分強力です](https://juliafolds2.github.io/Transducers.jl/dev/reference/manual/#Base.foreach)。
