```
ThinGratingInterface{T} <: OpticalInterface{T}
```

理想化された薄い格子を表すインターフェースです。`period`はマイクロメートル単位で、`vector`は表面の平面内にある必要があります。透過率と反射率は、`maxorder`および`minorder`パラメータを使用して最大10までの任意の次数に対して指定できます。`nothing`の場合、`reflectance`は**0**と仮定され、`transmission`は**1**と仮定されます。

```julia
ThinGratingInterface(vector, period, insidematerial, outsidematerial; maxorder = 1, minorder = -1, reflectance = nothing, transmission = nothing)
```
