```
mutable struct StructureReference{S, T} <: GeometryReference{S, T}
    structure::T
    origin::Point{S}
    xrefl::Bool
    mag::Float64
    rot::Float64
end
```

`origin` に位置する `structure` への参照で、オプションの x-反射 `xrefl`、拡大率 `mag`、および回転角 `rot` を持ちます。単位なしで角度が与えられた場合、それはラジアンであると見なされます。

つまり、参照によって適用される変換は、次の変換の合成であり、反射が最初に適用されます：

1. `xrefl(f)` が `true` の場合、`x` 軸に沿った反射
2. `rotation(f)` による回転
3. `mag(f)` による拡大
4. `origin(f)` による平行移動

型変数 `T` は循環定義を避けるためのものです。
