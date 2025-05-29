```
ParameterPlot(R::MultistartResults; st=:dotplot, BiLog::Bool=true, Nsteps::Int=5, StepTol::Real=1e-3, MaxValue=3000)
```

`MultistartResults`のパラメータ値をプロットし、異なる最適解が局所化されているかどうかを示すためにステップごとに分けます。`st`は`:dotplot`、`:boxplot`、または`:violin`のいずれかにすることができます。

!!! note
    このプロット関数を使用するには、StatsPlots.jlをロードする必要があります。

