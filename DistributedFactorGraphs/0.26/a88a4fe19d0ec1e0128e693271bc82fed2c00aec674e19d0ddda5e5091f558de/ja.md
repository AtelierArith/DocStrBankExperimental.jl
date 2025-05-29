```julia
loadDFG!(dfgLoadInto, dst; overwriteDFGMetadata)

```

保存されたフォルダーからDFGをロードします。

# 例

```julia
using DistributedFactorGraphs, IncrementalInference
# DFGを作成 - 直接作成することもできます。例えば、GraphsDFG{NoSolverParams}() または IIFを使用します:
dfg = initfg()
# グラフをロード
loadDFG!(dfg, "/tmp/savedgraph.tar.gz")
# 通常通りDFGを使用します。
ls(dfg)
```

参照: [`loadDFG`](@ref), [`saveDFG`](@ref)
