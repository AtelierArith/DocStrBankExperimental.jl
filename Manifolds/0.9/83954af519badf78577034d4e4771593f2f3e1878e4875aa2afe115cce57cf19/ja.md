```
identity_element(G::AbstractDecoratorManifold)
```

[`Identity`](@ref) の点表現を [`IsGroupManifold`](@ref) `G` に対して返します。デフォルトでは、この表現はデフォルトの配列または数値表現です。点が配列で表現されていない場合、`G` 上の点として $e$ の対応するデフォルト表現を返す必要があります。
