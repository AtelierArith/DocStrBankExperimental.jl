```
abstract type ContinuousHistogram end
```

`abstract type` は `ContinuousHistogram` 概念を表します。これらは、入力データに *不確実性* が関連付けられているヒストグラムであり、そのため各エントリに対して値-誤差依存カーネルを使用して構築します。

新しい `ContinuousHistogram` を作成する際には、`src/Kernels` フォルダ内の各関数をオーバーロードする必要があります。その後、新しい [`ContinuousDistribution`](@ref) を追加し、`src/Moments` ファイルに示されているようにそのメソッドを定義する必要があります。最後に、[`KernelDistribution`](@ref) をマッピングする必要があります。

その後、すべての `util` および `stats` 機能は *そのまま動作する* はずです。

!!! note
    この文脈における *連続性* は、ヒストグラムのドメインを指し、必ずしもその範囲を指すわけではありません。

