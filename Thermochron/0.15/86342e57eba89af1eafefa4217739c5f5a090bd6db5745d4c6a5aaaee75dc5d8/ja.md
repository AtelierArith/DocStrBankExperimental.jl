```julia
MDDiffusivity(
    D0::NTuple{N,T}             # [cm^2/sec] 最大拡散率
    D0_logsigma::NTuple{N,T}    # [単位なし] 対数不確実性 (デフォルト = 1/2 = ℯの2シグマの因子)
    Ea::T                       # [kJ/mol] 活性化エネルギー
    Ea_logsigma::T              # [単位なし] 対数不確実性 (デフォルト = 1/2 = ℯの2シグマの因子)
)
```

複数の領域に対する複数の拡散率
