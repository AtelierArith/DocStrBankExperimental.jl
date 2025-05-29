```julia
preambleCache(dfg, vars, usrfnc)

```

特定の因子前提使用のためのオーバーロード。

ノート：

  * https://github.com/JuliaRobotics/IncrementalInference.jl/issues/1462 を参照

開発ノート

  * CalcFactorに統合

      * スレッド処理を追加

例：

```julia
import IncrementalInference: preableCache

preableCache(dfg::AbstractDFG, vars::AbstractVector{<:DFGVariable}, usrfnc::MyFactor) = MyFactorCache(randn(10))

# 通常の使用を続ける、例えば
mfc = MyFactor(...)
addFactor!(fg, [:a;:b], mfc)
# ... 
```
