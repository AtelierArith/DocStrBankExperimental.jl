```
upreferred(x::Dimensions)
```

次元 `x` に対して推奨される単位を返します。ファクトリのデフォルトを使用している場合、この関数は基本SI単位の累乗の積を返します（[`Unitful.FreeUnits`](@ref)として）。
