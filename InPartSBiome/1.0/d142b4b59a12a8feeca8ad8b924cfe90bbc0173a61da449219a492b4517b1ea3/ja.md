```
SpheroidDiskCell
```

成長し運動するダンベルモデル。

[`DiskCell`](@ref)モデルに基づいており、いくつかの重要な違いがあります。

  * `orientationretention`パラメータを使用して、向きの継承を無効にできます。
  * 軸に沿ったペアワイズ細胞-細胞牽引力は、`motility`パラメータでスケーリングされます。
  * `basalreversalrate`パラメータを使用して、ランダムな方向反転が行われます。

モデルの詳細な説明については、[T. Sunkel, L. Hupe, and P. Bittihn, arXiv:2403.11002 (2024)](https://doi.org/10.48550/arXiv.2403.11002)を参照してください。

# 拡張ヘルプ

## フィールドのリスト

  * `id`, `centerpos`, `params`: InPartS標準フィールド
  * `nodeseparation`: 円形キャップの中心間で測定された細胞バックボーンの長さ
  * `φ`: 細胞バックボーンの向き
  * `growthprog`: 細胞の現在の成長段階
  * `grothrate`: `growthprog`の変化率
  * `attached`: trueに設定されている場合、すべての自由度（`growthprog`を除く）の進化が停止します。*現在は未使用*。
  * `P`, `N`: ノードの位置
  * `fP`, `fN`: ノードの力蓄積器
  * `reversaltimer`: 次の向き反転までの時間単位
  * `vtrans`, `ωspin`: 平行移動速度とスピン角速度
