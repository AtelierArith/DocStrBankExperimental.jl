dielectric(mod::LiquidSaltWater, T::FT,f::FT)

液体塩水の複素誘電率を計算します（Ulaby & Longの本）

# 引数

  * `mod` [`LiquidSaltWater`](@ref) 型の構造体、PSUでの塩分を提供
  * `T`  温度 `[⁰K]`
  * `f`  周波数 `[GHz]`
  * `S`  [`LiquidSaltWater`](@ref) 構造体からの塩分 `[PSU]`

# 例

```julia-repl
julia> w = CanopyOptics.LiquidSaltWater(S=10.0)     # 塩水の構造体を作成
julia> CanopyOptics.dielectric(w,283.0,10.0)
51.79254073931596 + 38.32304044382495im
```
