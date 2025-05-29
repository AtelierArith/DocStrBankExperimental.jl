```
climplot(A::ClimArray; kwargs...) → fig, ax, el, cb
```

主なプロット関数で、`A`に[`CoordinateSpace`](@ref)次元がある場合は[`climscatter!`](@ref)に、[`OrthogonalSpace`](@ref)の場合は[`climsurface!`](@ref)にディスパッチします。

図、軸、プロットされた要素、およびカラーバーを返します。

オプションでキーワード`scatter = true`を提供することで、散布図を強制的に使用することができます。

ClimateBase.jlからのプロットは、`ClimArray`を囲む`Observable`でも機能します。同じ空間次元を持つ別の`ClimArray`でobservableの値を更新すると、プロットが更新されます。例についてはオンラインのドキュメントを参照してください。
