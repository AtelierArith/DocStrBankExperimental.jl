```
DICE2023_NREG(n;kwargs...)
```

n等しい領域に分割されたDICE2023世界のパラメータを構築します（パラメータが上書きされない限り）。

世界がn地域に分割され、各地域が等しく、同じ係数を持ち、初期排出量、資本、生産、人口などが1/nであるパラメータ構造体を作成します。

データはDICE2013からのもので、`DICE2023_NREG(1)`の出力は`DICE2023()`と同じです。

キーワード引数を使用すると、DICE2023と異なる個別のパラメータを指定でき、最終的には地域ごとの仕様を持つことができます。

完全なパラメータのリストについては[`DICEParameters`](@ref)を、作成したパラメータ構造体を使用して最適化を実行するには[`run_dice`](@ref)を参照してください。

# 例

```julia
four_regions_parameters = DICE2023_NREG(4) 
alt_dam_parameters      = DICE2023_NREG(2, a2base = [0.01, 0.02]) # a2baseパラメータのみ異なる2地域
results = run_dice(four_regions_parameters)
```
