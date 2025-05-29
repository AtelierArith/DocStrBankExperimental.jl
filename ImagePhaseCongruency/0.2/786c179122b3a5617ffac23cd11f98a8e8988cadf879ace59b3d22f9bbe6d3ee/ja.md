方向選択周波数ドメインフィルタとコサインウィンドウ関数。

```
Usage: filter = cosineangularfilter(angl, wavelen, sintheta, costheta)

Arguments:
               angl - フィルタの方向（ラジアン）
            wavelen - Angularコサインウィンドウ関数の波長。
 sintheta, costheta - gridangles()によって返されるグリッド
```

参照: [`gaussianangularfilter`](@ref), [`filtergrids`](@ref)
