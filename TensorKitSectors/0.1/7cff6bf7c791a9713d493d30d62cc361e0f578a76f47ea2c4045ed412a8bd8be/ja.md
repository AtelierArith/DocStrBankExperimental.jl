```
struct FibonacciAnyon <: Sector
FibonacciAnyon(s::Symbol)
```

フィボナッチモジュラー融合カテゴリのアニオンを表します。これは、トリビアルセクター `FibonacciAnyon(:I)` と非トリビアルセクター `FibonacciAnyon(:τ)` に対応する2つの値を取ることができます。融合則は $τ ⊗ τ = 1 ⊕ τ$ です。

## フィールド

  * `isone::Bool`: セクターがトリビアルアニオン `:I` (`true`) に対応するか、非トリビアルアニオン `:τ` (`false`) に対応するかを示します。
