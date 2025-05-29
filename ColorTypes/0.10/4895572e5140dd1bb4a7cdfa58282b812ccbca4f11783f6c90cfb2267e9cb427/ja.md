```
C = ccolor(Cdest, Csrc)
```

`ccolor` ("コンクリートカラー") は、色空間と数値要素タイプの独立した選択をサポートします。`ccolor` は、利用可能な場合は `Cdest` から数値要素タイプを選択しますが、指定されていない場合は `Csrc` から取得します。

```jldoctest; setup = :(using ColorTypes, ColorTypes.FixedPointNumbers)
julia> ccolor(RGB, Gray{Float32})
RGB{Float32}

julia> ccolor(RGB, Gray{N0f8}) == RGB{N0f8}
true

julia> ccolor(RGB{Float32}, Gray{N0f8})
RGB{Float32}
```

一部の色空間は `FixedPoint` 数値要素タイプをサポートしていません。その場合、`Cdest` の `eltype_default` が選択されます。

```jldoctest; setup = :(using ColorTypes, ColorTypes.FixedPointNumbers)
julia> ccolor(HSV, RGB{N0f8})
HSV{Float32}
```

`Cdest` は抽象型であることができ、その場合 `Csrc` はその抽象色空間に属している必要があります。

```jldoctest; setup = :(using ColorTypes, ColorTypes.FixedPointNumbers)
julia> ccolor(Color{Float32}, RGB{N0f8})
RGB{Float32}

julia> ccolor(AbstractRGB{Float32}, BGR{N0f8})
BGR{Float32}

julia> ccolor(AbstractRGB{Float32}, HSV{Float32})
ERROR: in ccolor, empty intersection between AbstractRGB and HSV
[...]
```

`ccolor` は、明確なコンクリート型を決定できない場合にエラーをスローします。前のケースでは、`AbstractRGB{Float32}` は `RGB{Float32}` と `BGR{Float32}` を包含しています。

`ccolor` は他のメソッドを定義する際に最も便利です。たとえば、ユーザーが数値要素タイプを指定せずに `convert(RGB, c)` と書けるようにするには、次のように定義します。

```
convert(::Type{C}, p::Colorant) where C<:Colorant = cnvt(ccolor(C,typeof(p)), p)
```

ここで `cnvt` は明示的な変換を行う関数です。
