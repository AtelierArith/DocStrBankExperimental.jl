```
shrinkageplot(m::MixedModel, gf::Symbol=first(fnames(m)), θref, args...; kwargs...)
```

グループ化因子 `gf` のランダム効果の条件付き平均 b の散布図行列を返します。

推定されたパラメータ値での条件付き平均と `θref` での条件付き平均の2セットがプロットされます。デフォルトの `θref` は `Λ` が単位行列の非常に大きな倍数になる結果をもたらします。対応する条件付き平均はペナルティなしと見なすことができます。

`args...` と `kwargs...` は [`shrinkageplot!`](@ref) に渡されます。
