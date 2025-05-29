```
distortblock(
    B::F,
    Length::T,
    Width::T,
    nL::IT,
    nW::IT,
    xdispmul::T,
    ydispmul::T,
) where {F<:Function, T<:Number, IT<:Integer}
```

ブロックメッシュをノードを移動させることで歪めます。目的は、水平および垂直のメッシュラインを傾斜したラインに歪めることです。これは、特定の方向を避けなければならない有限要素をテストする際に便利です。
