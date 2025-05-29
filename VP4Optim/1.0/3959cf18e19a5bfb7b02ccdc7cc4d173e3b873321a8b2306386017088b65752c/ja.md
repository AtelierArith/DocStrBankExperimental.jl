```
∂∂Bb!(::Model)
```

`x` に関する二次の偏導関数を返します。

## デフォルト

  * なし、ユーザーによって提供される必要があります。

## 備考

  * 二次最適化手法に必要です。
  * `(B, b, ∂B, ∂b, ∂∂B, ∂∂b)::Tuple` を返します。
  * `(B, b, ∂B, ∂b)` は [∂Bb!](@ref ∂Bb!) から返されます。
  * 型: `∂∂B::SMatrix{Nx, Nx, SMatrix{Nc,Nc,T}}` および `∂∂b::SMatrix{Nx, Nx, SVector{Nc,T}}`
  * （または [fgh!](@ref fgh!) の実装で動作するものであれば何でも）
