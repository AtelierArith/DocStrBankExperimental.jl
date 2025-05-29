```Julia
earthgram(U::UnitSystem) = mass(milli,U,Meridian)
```

Meridian `gram` unit of `mass` based on `earthmeter` (kg or lb).

```Julia
julia> earthgram(Meridian) # keg
0.001

julia> earthgram(CGS) # g
1.0043504565319281

julia> earthgram(English) # lb
0.0022142137367344343

julia> earthgram(British) # slug
6.88198668206427e-5

julia> earthgram(Gravitational) # hyl
0.00010241524440373911
```
