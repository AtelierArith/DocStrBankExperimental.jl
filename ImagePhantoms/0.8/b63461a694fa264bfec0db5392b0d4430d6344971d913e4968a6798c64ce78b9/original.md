```
triangle(cx, cy, wx=1, wy=wx, ϕ=0, value::Number=1, param::Real=0.5)
triangle(center::NTuple{2,RealU}, width::NTuple{2,RealU}=(1,1), ϕ::RealU=0, v=1, param=0.5)
```

Construct `Object{Triangle}` from parameters. In the typical case where `param=0.5` and `width[1] == width[2]`, this is an equilateral triangle with base `width[1]` centered along the x axis.
