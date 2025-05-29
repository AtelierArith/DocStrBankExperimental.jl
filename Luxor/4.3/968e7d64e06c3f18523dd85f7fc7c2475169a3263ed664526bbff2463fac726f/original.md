```
@imagematrix! buffer drawing-instructions [width=256] [height=256]
```

Like `@imagematrix`, but use an existing UInt32 buffer.

```julia
w = 200
h  = 150
buffer = zeros(UInt32, w, h)
m = @imagematrix! buffer juliacircles(40) 200 150;
Images.RGB.(m)
```
