```
builtin_effects(𝕃::AbstractLattice, f::Builtin, argtypes::Vector{Any}, rt) -> Effects
```

ビルトイン関数呼び出しの効果を計算します。`argtypes` には `f` 自体は含めないでください。
