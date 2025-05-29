```
LE_to_ET(LE,Tair)
ET_to_LE(ET,Tair)
```

質量からエネルギー単位への蒸発水フラックスの変換 (ET=蒸発散) またはその逆。

# 引数

  * LE   潜熱フラックス (W m-2)
  * ET   蒸発散 (kg m-2 s-1)
  * Tair 空気温度 (℃)

# 詳細

変換は次のように与えられます：

  * $$
    ET = LE/\lambda
    $$
  * $$
    LE = \lambda ET
    $$

ここで、$\lambda$は蒸発潜熱 (J kg-1) であり、[`latent_heat_vaporization`](@ref) によって計算されます。

# 例

```jldoctest; output = false
# LEが200 Wm-2で、空気温度が25℃の場合
ET = LE_to_ET(200,25)
≈(ET, 8.19e-5, atol =1e-7)
# 出力
true
```
