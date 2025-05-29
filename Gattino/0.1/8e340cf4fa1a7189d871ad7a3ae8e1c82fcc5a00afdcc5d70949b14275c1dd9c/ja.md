```julia
set_shape!(con::AbstractContext, layer::String, into::Symbol; args ...) -> ::Nothing
```

`layer`内の各要素の形状を`into`に設定します。これは、コンポーネントの形状を再形成するために`ToolipsSVG.SVGShape`インターフェースを使用します。このAPIに組み込まれている利用可能な形状は...

  * `:square`
  * `:circle`
  * `:polyshape`
  * `:rect`
  * および`:star`

```example
newscatter = scatter([1, 2, 3], [1, 2, 3])
set_shape!(newscatter, "points", :star)
```
