```
DoubleBasis{Tb1<:AbstractBasis, Tb2<:AbstractBasis}
```

ある対称セクターから別の対称セクターへの遷移行列を構築するための基底。DoubleBasisは射影子として使用できるため、対称性の違反を無視します。したがって、この基底を扱う際には特に注意が必要です。

## 特性:

  * `dgt`: 桁数。
  * `B1` : 対象対称セクターの基底。
  * `B2` : 開始対称セクターの基底。
  * `B`  : 基本。
