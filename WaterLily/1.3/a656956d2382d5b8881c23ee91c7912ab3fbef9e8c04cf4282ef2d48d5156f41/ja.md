```
AutoBody(sdf,map=(x,t)->x; compose=true) <: AbstractBody
```

  * `sdf(x::AbstractVector,t::Real)::Real`: 符号付き距離関数
  * `map(x::AbstractVector,t::Real)::AbstractVector`: 座標マッピング関数
  * `compose::Bool=true`: `sdf=sdf∘map` を合成するためのフラグ

`sdf` とオプションの座標 `map` によって幾何学を暗黙的に定義します。注意: `compose=true` の場合、`map` は自動的に合成されます。すなわち、`sdf(x,t) = sdf(map(x,t),t)` です。それ以外の場合、両方のパラメータは独立のままです。複数のボディを組み合わせてより複雑なものを作成する際には、`compose=false` に設定することが特に役立ちます。
