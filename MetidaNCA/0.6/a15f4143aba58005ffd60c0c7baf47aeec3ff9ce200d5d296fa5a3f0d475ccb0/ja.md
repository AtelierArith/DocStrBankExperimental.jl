```
LimitRule(lloq::T, btmax, atmax, nan, rm::Bool) where T <: Real

LimitRule(;lloq = NaN, btmax = NaN, atmax = NaN, nan = NaN, rm::Bool = false)
```

  * `lloq` - LLOQ - 定量限の下限;
  * `btmax` - Tmax前のポイントの値;
  * `atmax` - Tmax後のポイントの値;
  * `nan` - `NaN`を置き換えるための値;
  * `rm` - `true`の場合、すべての`NaN`ポイントを削除します。

PK対象のルール。

  * ステップ 1 (NaNステップ): すべての`NaN`および`missing`値をnanキーワード値で置き換えます（`nan`がNaNでない場合）;
  * ステップ 2 (LLOQステップ): `lloq`がNaNでない場合、`lloq`未満の値をTmax前の場合は`btmax`値で、Tmax後の場合は`atmax`で置き換えます;
  * ステップ 3 (NaNを削除): `rm`がtrueの場合、すべての`NaN`および`missing`値を削除します。

参照: [`applylimitrule!`](@ref)
