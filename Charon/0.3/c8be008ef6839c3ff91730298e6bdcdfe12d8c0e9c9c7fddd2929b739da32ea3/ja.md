```
MCMCsampler(nchains::Integer, nsteps::Integer, prioronn::DiscreteUnivariateDistribution, prioronτCτA::ContinuousMultivariateDistribution, prioronϵ::ContinuousUnivariateDistribution, dicefile::IO, messages::Integer=nsteps÷100, scalingmessages::Bool=true, header::Bool=true)
```

dicefileはDICE 2-pop形式の開かれたCSVファイルです：正確に4列を含む必要があり、最初の列には祖先リードの数、2番目の列には派生リードの数、3番目の列にはアンカーポピュレーションにおける派生アレルの頻度、4番目の列にはこのデータの組み合わせを持つロキの数が含まれています。

Julia 1.3以上を使用している場合、ファイルが圧縮ファイルである場合は、zip解凍ツールを使用して開いてください：

```julia
using CodecZlib
dicefile = GzipDecompressorStream(open("path/to/your/file.csv.gz"))
```

名前付き引数「header」を使用して、CSVファイルにヘッダーがあるかどうかを示す必要があります。デフォルトはtrueです。
