```
interpolate(B, T, xi)
```

Given basis B, interpolate T at xi.

# Example

```jldoctest
B = Quad4()
X = Vec.([(0.0, 0.0), (1.0, 0.0), (1.0, 1.0), (0.0, 1.0)])
T = [1.0, 2.0, 3.0, 4.0]
interpolate(B, T, Vec(0.0, 0.0))

# output

2.5
```
