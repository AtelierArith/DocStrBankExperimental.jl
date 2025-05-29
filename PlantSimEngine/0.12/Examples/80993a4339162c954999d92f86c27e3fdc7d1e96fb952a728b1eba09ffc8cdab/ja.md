```
fit(::Type{Beer}, df; J_to_umol=PlantMeteo.Constants().J_to_umol)
```

測定値からビール・ランバートの法則の `k` パラメータを計算します。

# 引数

  * `::Type{Beer}`: モデルタイプ
  * `df`: 次の列を持つ `DataFrame`:

      * `aPPFD`: μmol[PAR] m[leaf]⁻² s⁻¹ で測定された吸収された光合成光子フラックス密度
      * `LAI`: m² m⁻² で測定された葉面積指数
      * `Ri_PAR_f`: W m[soil]⁻² (== J m[soil]⁻² s⁻¹) で測定された大気放射の入射フラックス

# 例

`Examples` サブモジュールで定義された例のモデルをインポートします:

```julia
using PlantSimEngine
using PlantSimEngine.Examples
```

ビールモデルを持つモデルリストを作成し、データにフィットさせます:

```julia
m = ModelList(Beer(0.6), status=(LAI=2.0,))
meteo = Atmosphere(T=20.0, Wind=1.0, P=101.3, Rh=0.65, Ri_PAR_f=300.0)
run!(m, meteo)
df = DataFrame(aPPFD=m[:aPPFD][1], LAI=m.status.LAI[1], Ri_PAR_f=meteo.Ri_PAR_f[1])
fit(Beer, df)
```
