コールバック関数のプロトタイプは、パーティショニングのための重みを計算します。

!!! note
    重みのグローバル合計は64ビット整数に収まる必要があります。


### パラメータ

  * `p4est`:[in] 森
  * `which_tree`:[in] *クアドラント*を含む木

### 戻り値

0以上の32ビット整数としてのクアドラントの重み。
