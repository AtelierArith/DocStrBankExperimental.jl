```
StatsModels.ContrastsCoding(mat::AbstractMatrix[, levels]])
StatsModels.ContrastsCoding(mat::AbstractMatrix[; levels=nothing])
```

コントラスト行列の手動指定によるコーディング。kレベルの場合、コントラストはk x k-1の行列でなければなりません。この行列のコントラストはモデル行列に直接コピーされます。各レベルのセル平均に割り当てられた重みとしてコントラストを仮説として指定したい場合は、[`HypothesisCoding`](@ref)を使用する必要があります。
