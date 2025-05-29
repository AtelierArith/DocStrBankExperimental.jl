```julia
loadDFG!(
    dfgLoadInto,
    dst;
    overwriteDFGMetadata,
    useDeprExtract
)

```

保存されたフォルダからDFGをロードします。

# 例

```julia
using DistributedFactorGraphs, IncrementalInference
# DFGを作成 - 直接作成することもできます。例えば、GraphsDFG{NoSolverParams}() または IIFを使用します:
dfg = initfg()
# グラフをロードします
loadDFG!(dfg, "/tmp/savedgraph.tar.gz")
# 通常通りDFGを使用します。
ls(dfg)
```

関連情報: [`loadDFG`](@ref), [`saveDFG`](@ref)
