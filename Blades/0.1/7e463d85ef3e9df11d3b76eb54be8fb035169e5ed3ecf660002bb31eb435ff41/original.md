```
ZForm{D}(f,df)
```

Differential 0-form Represents a scalar function to be evaluated at a point.  Takes a vector returns a scalar. df is a list of partial  The index is that of the coordinate basis 1-form D is the dimensionality of the coordinate basis 1-forms

Example: julia> dist(x,y) = ZForm(()->(sqrt(x^2+y^2)), (i)->[x/sqrt(x^2+y^2), y/sqrt(x^2+y^2)][i])

julia> dist(1.0,-1.0).df(2) -0.7071067811865475

julia> dist(1.0,-1.0).df(1) 0.7071067811865475

julia> dist(1.0,-1.0).f() 1.4142135623730951
