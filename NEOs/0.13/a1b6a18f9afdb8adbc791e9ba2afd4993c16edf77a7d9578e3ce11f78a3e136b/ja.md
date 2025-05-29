```
bwdfwdeph(t::U, bwd::TaylorInterpolant, fwd::TaylorInterpolant
    [, et::Bool [, kmsec::Bool]]) where {U <: Number}
```

時間 `t` における天体暦を評価します。ここで、`bwd`（`fwd`）は後方（前方）伝播です。

## オプション引数

  * `et::Bool`: `t` がJ2000からの天体秒であるかどうか（デフォルト: `true`）。
  * `kmsec::Bool`: 状態ベクトルを [km, km/s] に変換するかどうか（デフォルト: `true`）。
