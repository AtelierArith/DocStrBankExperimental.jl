```julia
Plot_History(sc::SelfCons{T, R, S}, arg::String ; indices::Vector{Int64} = collect(1:length(sc.Initial)), plot_legend::Bool = true) where {T<:Function, R<:Function, S<:Union{Number, Vector{<:Number}}}
```

`sc.VIns`、`sc.VOuts`、または反復の関数としての収束をプロットするためのプロット関数。`arg` が "inputs"、"outputs"、または "convergence" の場合、それぞれに対応します。オプションの引数 `indices` は、ベクトル引数のサブセットのみをプロットしたい場合に使用します。`log_plot` は、収束と反復の半対数プロットをプロットしたい場合に使用します。
