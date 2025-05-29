```
RICE2023(;kwargs...)
```

DICE2023の世界合計と12地域のRICE2020地域分布に合わせて調整されたビルドパラメータを作成します。

世界を12の地域に分割し、DICE2023の係数を持つパラメータ構造体を作成しますが、地域の分散はほとんどの場合RICE2020（初期排出量、資本、生産、人口）から導出されるか、仮定されます（例：損害）。

各地域に提供する効用重みは外生的であり（デフォルトは等しい重み）、Negishi重みではありません。`run_dice`関数は、これらの重みを探すために反復的に使用されることがあります。

完全なパラメータのリストについては[`DICEParameters`](@ref)を、作成したパラメータ構造体を使用して最適化を実行するには[`run_dice`](@ref)を参照してください。

# 例

```julia
w_rich  = [5,4,3,3,1,1,3,2,2,1,1.5,1] #
w_equal = fill(1,12)
res_cbopt_12r_poor = run_dice(RICE2023(;weights=w_poor))
res_cbopt_12r_rich = run_dice(RICE2023(;weights=w_rich)) 
```

# 注記

  * デフォルトの12地域は次の通りです: ["USA", "EUS", "JPN", "OHI", "RUS", "EEC", "CHN", "IND", "MDE", "SSA", "LAA", "ROW"]
