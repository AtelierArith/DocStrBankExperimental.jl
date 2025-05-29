```
singlephase38linesInputs(;
    Pload=Dict{String, AbstractArray{Real, 1}}(), 
    Qload=Dict{String, AbstractArray{Real, 1}}(), 
    T=24,
    loadnodes = ["3", "5", "36", "9", "10", "11", "12", "13", "15", "17", "18", "19", "22", "25", 
                "27", "28", "30", "31", "32", "33", "34", "35"],
    Sbase = 1e6,
    Vbase = 12.5e3,
    v0=1.0,
    v_uplim = 1.05,
    v_lolim = 0.95,
)
```

38本のラインとノードを持つ単相ネットワークを作成するための便利な関数。出典: Andrianesis et al. 2019 "Locational Marginal Value of Distributed Energy Resources as Non-Wires Alternatives"

Inputsは可変構造体であることに注意してください（後で負荷を追加できます）。
