```
setelement!(mvis::MechanismVisualizer, element::VisualElement, name::AbstractString="<element>")
```

指定されたビジュアル要素をビジュアライザーに添付します。要素のフレームは、その幾何学がシーンツリーにどのように接続されるかを決定しますので、同じボディに接続された他のすべての幾何学が一緒に移動します。
