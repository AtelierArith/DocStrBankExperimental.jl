```
Inputs(
    edges::Array{Tuple}, 
    linecodes::Array{String}, 
    linelengths::Array{Float64}, 
    phases::Vector{Vector},
    substation_bus::String;
    Pload, 
    Qload, 
    Sbase=1, 
    Vbase=1, 
    Zdict, 
    v0, 
    v_lolim=0.95, 
    v_uplim=1.05,
    Ntimesteps=1, 
    P_up_bound=1e4,
    Q_up_bound=1e4,
    P_lo_bound=-1e4,
    Q_lo_bound=-1e4,
    Isquared_up_bounds=Dict{String, Float64}(),
    relaxed=true
)
```

最も低いレベルの Inputs コンストラクタ（Inputs 構造体を返す唯一のもの）。

!!! note
    提供された実負荷と無効負荷は `Sbase` を使用して正規化されています。

