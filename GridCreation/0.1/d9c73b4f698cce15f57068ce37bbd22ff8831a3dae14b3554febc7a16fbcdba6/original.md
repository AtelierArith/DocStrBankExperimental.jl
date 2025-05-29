```
mkCartVecs(dx, size[, center])
```

Create a 2D "grid" by returning a row vector x and column vector y.

The grid will have sample spacing dx, size[0] == size(x), and size[1] == size(y).

If size is an int, it is broadcast to [size,size].

The grid will be centered according to such that the center element contains zero.  Special values for center include -1 (default, FFT-like center) and -2, for "interpixel" sampling, where 0 is at size/2.  Otherwise, zero is at the centerth element.

The centering rule may not be different between x and y.

# Examples

## FFT-aligned grid

Note that the ceil rounded center element contains zero.

```julia-repl
julia> x,y = mkCartVecs(.1, 4); # implicit center=CFFT
julia> x
1×4 LinearAlgebra.Adjoint{Float64,StepRangeLen{Float64,Base.TwicePrecision{Float64},Base.TwicePrecision{Float64}}}:
 -0.2  -0.1  0.0  0.1
julia> collect(y)
4-element Array{Float64,1}:
 -0.2
 -0.1
  0.0
  0.1
```

## Intersample aligned grid

```julia-repl
x,y=mkCartVecs(.1, 4, center=CInterSample);

julia> x
1×4 LinearAlgebra.Adjoint{Float64,StepRangeLen{Float64,Base.TwicePrecision{Float64},Base.TwicePrecision{Float64}}}:
 -0.15  -0.05  0.05  0.15
```

## index-centered grid

```
julia> x,y=mkCartVecs(.1, 4, center=1);
julia> x
1×4 LinearAlgebra.Adjoint{Float64,StepRangeLen{Float64,Base.TwicePrecision{Float64},Base.TwicePrecision{Float64}}}:
 1.11022e-17  0.1  0.2  0.3
```
