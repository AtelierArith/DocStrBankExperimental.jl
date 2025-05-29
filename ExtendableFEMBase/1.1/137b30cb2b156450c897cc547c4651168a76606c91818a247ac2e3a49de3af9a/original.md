```
function continuify(
	source::FEVectorBlock,
	operator = Identity;
	abs::Bool = false,
	broken = false,
	order = "auto",
	factor = 1,
	regions::Array{Int,1} = [0]) where {T,Tv,Ti,FEType,APT}
```

interpolates operator evaluation of source into a FE function of FEType H1Pk, i.e., Lagrange interpolation of arbitrary  operator evaluations of the source finite element type, broken = true generates a piecewise interpolation
