```
upscale(a::Generic.LaurentSeriesElem{T}, n::Int) where T <: RingElement
```

基礎となる多項式を$n$の因子で縮小します。これにより、パディングのために存在していたゼロ係数が削除されます。$a$の非ゼロ係数の間隔が$n$で割り切れると仮定します。
