```
sref(x::GeometryStructure{T}, origin=zero(Point{T}); kwargs...)
```

`StructureReference{float(T), typeof(x)}`の便利なコンストラクタです。

これらのキーワードには同義語が受け入れられます：

```
- X反射: `:xrefl`, `:xreflection`, `:refl`, `:reflect`, `:xreflect`,
`:xmirror`, `:mirror`
- 拡大: `:mag`, `:magnification`, `:magnify`, `:zoom`, `:scale`
- 回転: `:rot`, `:rotation`, `:rotate`, `:angle`
```
