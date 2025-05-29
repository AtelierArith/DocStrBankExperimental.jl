`ExponentialQueueDict{K}` は、定数レート Q[k] を持つ要素のタイプ `K` の更新可能なキューを保持します。これは連続時間でのサンプリングを目的としています。

```julia
julia> Q = ExponentialQueueDict{Int}() 
ExponentialQueueDict(Pair{Int64, Float64}[])
```

```julia
julia> Q[1] = 1.2 # イベント 1 のレートを更新 1.2
```

```julia
julia> Q[55] = 2.3 # イベント 55 のレートを更新 2.3
```

```julia
julia> i,t = pop!(Q) # 次のイベントの時間とIDを取得し、キューから削除します (55, 0.37869716808319576)
```

関連情報: `StaticExponentialQueue` と `ExponentialQueue` は、`K == Int` の場合に対してわずかに効率的なキューです。
