```
makeswarm_genes(genes::Vector{String}; <keyword arguments> )
```

遺伝子ベクトル genes の各遺伝子を実行するための swarmfile と fit ファイルを作成します。

# 引数

  * `genes`: 遺伝子のベクトル
  * `batchsize=1000`: swarmfile あたりのジョブ数、デフォルト = 1000

および makeswarm(;<keyword arguments>) のすべての引数

```
例
```

julia> genes = ["MYC","SOX9"]

julia> makeswarm(genes,cell="HBEC")
