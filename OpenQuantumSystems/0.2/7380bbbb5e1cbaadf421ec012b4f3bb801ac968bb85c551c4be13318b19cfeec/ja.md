```
Molecule{T,C1,C2}(modes, Nvib, E)
```

[`Aggregate`](@ref)内の分子をモデル化するための構造体です。

# 引数

  * `modes`: モードのベクター ([`Mode`](@ref))。
  * `Nvib`: すべてのモードの最大振動状態数。
  * `E`: 分子の基底状態および励起状態のエネルギー（HOMO、LUMO）。
