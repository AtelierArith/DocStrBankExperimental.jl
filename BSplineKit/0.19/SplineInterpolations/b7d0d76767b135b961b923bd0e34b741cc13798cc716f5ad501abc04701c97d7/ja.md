```
interpolate!(I::SplineInterpolation, y::AbstractVector)
```

新しいデータでスプライン補間を更新します。

この関数は、以前の[`interpolate`](@ref)の呼び出しによって返された[`SplineInterpolation`](@ref)を再利用し、同じ位置`x`で新しいデータを使用することを可能にします。

詳細については[`interpolate`](@ref)を参照してください。
