```
function ZeroValue(::Nothing)
function ZeroValue(units::Vector{Unitful.FreeUnits{N, D, nothing} where D where N} = uAstro)
```

対応する `units` でゼロの `Measurement` 値を提供する不変構造体を構築します（デフォルトは `uAstro`）。単位がない場合は `nothing` を使用します。累積合計、配列の初期化などに便利です。

# 例

```
ZeroValue(nothing)
ZeroValue()
ZeroValue(uSI)
ZeroValue(uCGS)
```
