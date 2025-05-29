```
RodCellParams
```

[`RodCell`](@ref)のパラメータ。

モデルの説明については、[J. Isensee et al., J. R. Soc. Interface. 19, 20220512 (2022)](https://doi.org/10.1098/rsif.2022.0512)を参照してください。

# 拡張ヘルプ

## フィールドのリスト

  * `maxlength`: 成熟した細胞のノード間隔 (growthprog → 1)
  * `radius`: 半径。
  * `youngsmodulus`: 細胞の硬さ
  * `inthardnessfactor`: 外部の硬さに対する内部の硬さ。デフォルト値は `1.0`。
  * `viscosity`: 細胞の移動性を均等にスケールします
  * `intmobilityfactor`: 平行移動と内部移動の比率を設定します。
  * `growthrateretention`: 子の成長率の継承成分の重み
  * `growthratedistribution`: 子の成長率のランダム成分の分布
