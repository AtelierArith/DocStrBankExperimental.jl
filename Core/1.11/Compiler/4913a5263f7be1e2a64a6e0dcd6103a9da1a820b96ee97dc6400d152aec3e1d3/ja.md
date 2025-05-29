```
builtin_nothrow(𝕃::AbstractLattice, f::Builtin, argtypes::Vector{Any}, rt) -> Bool
```

ビルトイン関数呼び出しのスロー性を計算します。`argtypes` には `f` 自体は含めないでください。
