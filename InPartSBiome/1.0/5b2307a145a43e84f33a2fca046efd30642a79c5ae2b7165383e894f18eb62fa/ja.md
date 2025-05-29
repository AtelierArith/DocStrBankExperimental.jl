```
SpheroidDiskCellParams
```

[`SpheroidDiskCell`](@ref)のパラメータ。

モデルの詳細な説明については、[T. Sunkel, L. Hupe, and P. Bittihn, arXiv:2403.11002 (2024)](https://doi.org/10.48550/arXiv.2403.11002)を参照してください。

# 拡張ヘルプ

## フィールドのリスト

  * `motility`: 細胞間の牽引力をスケーリングします
  * `radius`: 半径。
  * `youngsmodulus`: 細胞の硬さ
  * `inthardnessfactor`: 外部の硬さに対する内部の硬さ。デフォルト値は `1.0` です。
  * `viscosity`: 細胞の移動性を均一にスケーリングします
  * `intmobilityfactor`: 平行移動と内部移動の比率を設定します。
  * `growthrateretention`: 子の成長率の継承成分の重み
  * `growthratedistribution`: 子の成長率のランダム成分の分布
  * `orientationretention`: 親の向きが子の向きに与える影響を設定します。現在、`Inf`（完全な継承）または `0`（無相関のランダムな向き）のみを受け入れます。
  * `basalreversalrate`: 向きの反転率を設定します

```
