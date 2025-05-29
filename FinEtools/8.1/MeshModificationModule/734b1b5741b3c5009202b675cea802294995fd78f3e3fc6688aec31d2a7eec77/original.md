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

Distort a block mesh by shifting around the nodes. The goal is to distort the horizontal and vertical mesh lines into slanted lines. This is useful when testing finite elements where special directions must be avoided.
