```
arclength(X)
```

Fetch or compute the arc length of the curve or path `X`.

# Example

```
julia> ellipse = ClosedCurve( t->cos(t)+2im*sin(t), 0,2π );
julia> arclength(ellipse)  # good to about 10 digits
9.688448219981513
```
