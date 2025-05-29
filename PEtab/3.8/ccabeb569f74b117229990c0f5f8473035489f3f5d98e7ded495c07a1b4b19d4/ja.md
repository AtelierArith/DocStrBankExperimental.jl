```
calibrate_multistart(prob::PEtabODEProblem, alg, nmultistarts::Integer; nprocs = 1,
                     dirsave=nothing, kwargs...)::PEtabMultistartResult
```

`alg`最適化アルゴリズムを使用して、`prob`内の未知のモデルパラメータを推定するために、ランダムにサンプリングされた開始点から`nmultistarts`パラメータ推定実行を行います。

利用可能で推奨される最適化アルゴリズム（`alg`）のリストは、パッケージのドキュメントおよび[`calibrate`](@ref)ドキュメントにあります。

`nprocs > 1`の場合、パラメータ推定実行は、Distributed.jlの[`pmap`](https://docs.julialang.org/en/v1/stdlib/Distributed/#Distributed.pmap)関数を使用して、`nprocs`プロセスで並行して実行されます。単一プロセス（`nprocs = 1`）でのパラメータ推定に5分以上かかる場合は、**強く**`nprocs > 1`を設定することをお勧めします。これにより、実行時間が大幅に短縮される可能性があります。`nprocs`はコンピュータのコア数より大きくしてはいけません。

`dirsave`が提供されている場合、各実行の中間結果は`dirsave`に保存されます。パラメータ推定には数時間（または数日！）かかる可能性があるため、大きなモデルの場合は`dirsave`を提供することを**強く**お勧めします。`dirsave`がない場合、何か問題が発生した場合にすべての中間結果が失われます。

パラメータ推定結果を視覚化するためのさまざまな方法は、ドキュメントに記載されています。

また、[`PEtabMultistartResult`](@ref)、[`get_startguesses`](@ref)、および[`calibrate`](@ref)も参照してください。

## キーワード引数

  * `sampling_method = LatinHypercubeSample()`: 多様（広がった）な開始点のセットをサンプリングするための方法。サンプリングに使用される関数である[`get_startguesses`](@ref)のドキュメントを参照してください。
  * `sample_prior::Bool = true`: [`get_startguesses`](@ref)のドキュメントを参照してください。
  * `seed = nothing`: 開始点を生成する際に使用されるシード。
  * `options = DEFAULT_OPTIONS`: `alg`のための設定可能なオプション。[`calibrate`](@ref)のドキュメントを参照してください。
