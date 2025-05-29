方向選択的周波数領域フィルターとガウス窓関数。

```
Usage: filter = gaussianangularfilter(angl, thetaSigma, sintheta, costheta)

Arguments:
               angl - フィルターの方向（ラジアン）
         thetasigma - Angular Gaussian 窓関数の標準偏差。
 sintheta, costheta - gridangles() によって返されるグリッド
```

参照: [`cosineangularfilter`](@ref), [`gridangles`](@ref), [`filtergrids`](@ref)
