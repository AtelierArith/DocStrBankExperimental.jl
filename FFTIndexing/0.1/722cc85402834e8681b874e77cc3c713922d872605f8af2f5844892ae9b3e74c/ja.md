```
FFTAxis <: AbstractVector{Int}
```

`FFTIndices`の1次元の対応物であり、単一の次元のみをサポートします。その要素は`FFTIndices`の`CartesianIndex`ではなく、通常の`Int`型です。

この型は、通常`axes`によって返される`Base.OneTo`のアナログとして機能します。このパッケージは、同じ目的を果たすために`fftaxes`を提供します。

# 例

```
julia> FFTAxis(4)
4-element FFTAxis:
 0
 1
 -2
 -1
```
