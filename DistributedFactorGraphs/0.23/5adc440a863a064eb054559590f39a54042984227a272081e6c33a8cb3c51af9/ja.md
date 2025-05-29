```julia
saveDFG(folder, dfg; saveMetadata)

```

DFGをフォルダーに保存します。フォルダーが存在する場合は作成/上書きします。

DevNotes:

  * TODO `compress` kwargを削除します。

# 例

```julia
using DistributedFactorGraphs, IncrementalInference
# DFGを作成します - 直接作成することもできます。例えば、GraphsDFG{NoSolverParams}()またはIIFを使用します：
dfg = initfg()
# ... IIFまたはDFGを使用してグラフに要素を追加します：
v1 = addVariable!(dfg, :a, ContinuousScalar, tags = [:POSE], solvable=0)
# それを保存します：
saveDFG(dfg, "/tmp/saveDFG.tar.gz")
```
