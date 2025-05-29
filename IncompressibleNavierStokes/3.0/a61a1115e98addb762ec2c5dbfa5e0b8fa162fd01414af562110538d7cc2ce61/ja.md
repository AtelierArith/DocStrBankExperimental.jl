```julia
struct LMWray3{T} <: IncompressibleNavierStokes.AbstractRungeKuttaMethod{T}
```

低メモリ Wray 3次スキーム。3つのベクトル場と1つのスカラー場を使用します。

## フィールド
