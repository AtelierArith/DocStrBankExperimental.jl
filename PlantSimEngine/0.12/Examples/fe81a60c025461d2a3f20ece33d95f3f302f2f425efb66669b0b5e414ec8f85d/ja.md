```
run!(::Beer, object, meteo, constants=Constants(), extra=nothing)
```

オブジェクトによって吸収される光合成光子フラックス密度（`aPPFD`、µmol m⁻² s⁻¹）を、入射PAR放射フラックス（`Ri_PAR_f`、W m⁻²）と光の消失に関するビール・ランバートの法則を使用して計算します。

# 引数

  * `::Beer`: モデルリストからのビールモデル（*すなわち* m.light_interception）
  * `models`: モデルのパラメータを保持する`ModelList`構造体で、`LAI`（m² m⁻²）の初期化を含みます：葉面積指数。
  * `status`: モデルの状態、通常はモデルリストの状態（*すなわち* m.status）
  * `meteo`: 気象構造体、[`Atmosphere`](https://palmstudio.github.io/PlantMeteo.jl/stable/#PlantMeteo.Atmosphere)を参照
  * `constants = PlantMeteo.Constants()`: 物理定数。詳細については`PlantMeteo.Constants`を参照
  * `extra = nothing`: 追加の引数、ここでは使用されません。

# 例

```julia
m = ModelList(Beer(0.5), status=(LAI=2.0,))

meteo = Atmosphere(T=20.0, Wind=1.0, P=101.3, Rh=0.65, Ri_PAR_q=300.0)

run!(m, meteo)

m[:aPPFD]
```
