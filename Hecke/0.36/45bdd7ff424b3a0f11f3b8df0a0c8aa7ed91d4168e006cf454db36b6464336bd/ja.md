```
relative_residue_field(O::RelNumFieldOrder, P::RelNumFieldOrderIdeal) -> RelFinField, Map
```

相対数体 $E/K$ における最大の整域 `O` と `O` の素イデアル `P` が与えられたとき、残差体 $O/P$ を、`K` の最大の整域における（相対的な）残差体の拡張として返します。`minimum(P)` における残差体を考慮してください。

`K` が相対数体である場合、後者も相対残差体として見なされることに注意してください。
