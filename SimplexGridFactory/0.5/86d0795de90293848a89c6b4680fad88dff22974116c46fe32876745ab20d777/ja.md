```
function simplexgrid(Generator;
                     points=Array{Cdouble,2}(undef,0,0),
                     bfaces=Array{Cint,2}(undef,0,0),
                     bfaceregions=Array{Cint,1}(undef,0),
                     regionpoints=Array{Cdouble,2}(undef,0,0),
                     regionnumbers=Array{Cint,1}(undef,0),
                     regionvolumes=Array{Cdouble,1}(undef,0);
                     kwargs...
                  )
```

入力配列の数からグリッドを作成します。2D入力配列は必要に応じて転置され、TriangulateまたはTetGen用の適切なデータ型に変換されます。

この変換は、データ型がデフォルトで示されているものであり、2D配列の先頭次元が空間次元に対応している場合には行われません。

利用可能な`kwargs`については、[`default_options`](@ref)を参照してください。
