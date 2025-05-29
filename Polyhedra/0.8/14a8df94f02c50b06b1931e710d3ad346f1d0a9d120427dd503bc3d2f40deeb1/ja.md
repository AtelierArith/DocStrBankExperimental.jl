```
removevredundancy!(p::VRep; strongly=false, planar=true, kws...)
```

`p`のV表現の要素を削除します。これは、`p`が表す多面体を変更することなく削除できる要素です。つまり、極点とレイのみを保持します。この操作は、残りの点が初期の点の集合の凸包の極点であるため、「凸包」と呼ばれることがよくあります。`strongly=true`の場合、弱冗長点、すなわち極点ではないが相対内部にもない点が保持されることがあります。`fulldim(p)`が2で、`strongly`が`false`、`planar`が`true`の場合、平面凸包アルゴリズムが使用されます。

残りのキーワード引数`kws`は、[`detectvlinearity!`](@ref)および[`detecthlinearity!`](@ref)に渡されます。
