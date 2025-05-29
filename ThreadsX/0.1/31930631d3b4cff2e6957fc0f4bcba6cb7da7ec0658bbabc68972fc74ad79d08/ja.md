# Threads⨉: 並列化された `Base` 関数

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliafolds2.github.io/ThreadsX.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliafolds2.github.io/ThreadsX.jl/dev)

## tl;dr

`Base` の関数に `ThreadsX.` プレフィックスを追加することで、サポートされている場合に速度向上が得られます。例:

```jldoctest ThreadsX
julia> using ThreadsX

julia> ThreadsX.sum(gcd(42, i) == 1 for i in 1:10_000)
2857
```

ThreadsX.jl によってサポートされている関数を見つけるには、REPL で `ThreadsX.` + *TAB* を入力してください:

```julia
julia> ThreadsX.
MergeSort       any             findfirst       map!            reduce
QuickSort       collect         findlast        mapreduce       sort
Set             count           foreach         maximum         sort!
StableQuickSort extrema         issorted        minimum         sum
all             findall         map             prod            unique
```

## 相互運用性

### 豊富なコレクションサポート

`reduce` ベースの関数は、配列、`Dict`、`Set`、およびイテレータ変換を含む [`SplittablesBase.jl`](https://github.com/JuliaFolds2/SplittablesBase.jl) インターフェースを実装する任意のコレクションをサポートします。特に、これらの関数はイテレータ内包表記をサポートします:

```jldoctest ThreadsX
julia> ThreadsX.sum(y for x in 1:10 if isodd(x) for y in 1:x^2)
4917
```

高度な使用法では、並列化可能なトランスデューサーで構築された [`Transducers.eduction`](https://juliafolds2.github.io/Transducers.jl/dev/reference/manual/#Transducers.eduction) もサポートします。

### OnlineStats.jl

`ThreadsX.reduce` は、[OnlineStats.jl](https://github.com/joshday/OnlineStats.jl) からの `OnlineStat` を最初の引数としてサポートします。これは、[マージインターフェース](https://github.com/joshday/OnlineStatsBase.jl#interface) を実装している限りです:

```jldoctest ThreadsX
julia> using OnlineStats: Mean

julia> ThreadsX.reduce(Mean(), 1:10)
Mean: n=10 | value=5.5
```

## API

ThreadsX.jl は、Julia プログラムを簡単に並列化するために `Base` 関数と互換性のある API を提供することを目指しています。

`ThreadsX` 名前空間の下に直接存在するすべての関数は公開 API であり、`Base` によって提供される API のサブセットを実装しています。`ThreadsX.Implementations` 内のすべては実装の詳細です。`ThreadsX` の公開 API 関数は、引数として渡されるデータ構造と関数が「スレッドフレンドリー」であることを期待しています。これは、与えられたコンテナ内の*異なる*要素に対して複数のタスクが並行して操作することが安全であることを意味します。たとえば、`ThreadsX.sum(f, array)` は、複数のスレッドから `f(::eltype(array))` を実行し、`array[i]` のように要素にアクセスすることが安全であると仮定しています。特に、`array` が不変オブジェクトの `Vector` であり、`f` がグローバルオブジェクトを変更しない純粋な関数である場合、これは当てはまります。`array[i]` へのアクセスをロックで保護する「スレッドセーフ」な配列を使用することは必須ではなく、*推奨されません*。

`Base` API に加えて、すべての関数は、各スレッドによって処理される要素の数を構成するためにキーワード引数 `basesize::Integer` を受け入れます。大きな値は、複数のスレッドを使用する際のオーバーヘッドを最小限に抑えるのに役立ちます。小さな値は、単一のアイテムを処理する時間がアイテムごとに大きく異なる場合の負荷分散に役立ちます。各関数の `basesize` のデフォルト値は現在、実装の詳細です。

ThreadsX.jl API は、同じ入力が同じ出力を生成するという意味で決定論的です。これは、`julia` のタスクスケジューラがタスクを実行する方法に依存しません。ただし、`basesize` は `Threads.nthreads()` に基づいて設定される可能性のある入力の一部であることに注意してください。計算の結果を `Threads.nthreads()` の値に依存しないようにするには、`basesize` を明示的に指定する必要があります。

## 制限事項

  * キーワード引数 `dims` はまだサポートされていません。
  * (おそらく他にもあります。)

## 実装

ほとんどの `reduce` ベースの関数は、[`Transducers.jl`](https://github.com/JuliaFolds2/Transducers.jl) の薄いラッパーとして実装されています。

カスタムコレクションは、[`SplittablesBase.jl`](https://github.com/JuliaFolds2/SplittablesBase.jl) インターフェースを実装することで ThreadsX.jl API をサポートできます。
