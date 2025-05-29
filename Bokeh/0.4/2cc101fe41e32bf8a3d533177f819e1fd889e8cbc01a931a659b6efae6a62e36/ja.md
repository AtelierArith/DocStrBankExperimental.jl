```
js_on_change(model, event, callbacks...)
```

任意の BokehJS モデルの変更イベントに [`CustomJS`](@ref) コールバックを添付します。

モデルプロパティの変更イベントは `"change:property_name"` の形式ですが、便利さのために単に `"property_name"` を提供することもできます。
