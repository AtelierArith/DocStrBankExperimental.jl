```
post_crush(pr::PresolveResult{T}, x::Vector{T}; is_ray::Bool=false)
```

事前解決モデルから元のモデルへの点をマッピングします。`is_ray = false` の場合、点は事前解決モデルの実行可能な点である必要があります。それ以外の場合は、無限大のレイである必要があります。

注意: `x` の長さが事前解決モデルの変数の数と等しくない場合、エラーが発生します。
