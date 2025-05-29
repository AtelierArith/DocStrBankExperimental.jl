```
Regularize(x,y,dx,[ddftype=Yang3],[graddir=0],[I0=(1,1)], [weights=1.0], [filter=false],
                   [issymmetric=false])
```

Constructor to set up an operator for regularizing and interpolating data from/to points immersed in the grid to/from fields on the grid itself. The supplied `x` and `y` represent physical coordinates of the immersed points, and `dx` denotes a uniform physical cell size of the grid. The separate arguments `x` and `y` can be replaced by a single argument `X` of type `VectorData` holding the coordinates.

The operations of regularization and interpolation are carried out with a discrete delta function (ddf), which defaults to the type `Yang3`. Others are also possible, such as `Roma`, `Goza` or `M3`. The optional argument `graddir`, if set to 1 or 2, will generate an interpolation operator that evaluates the negative of the respective component of the gradient of a grid field at the immersed points. The default value of this argument is 0, which simply interpolates. Note that the regularization form of this gradient type is also possible.

The optional tuple `I0` represents the indices of the primary node that coincides with `(x,y) = (0,0)`. This defaults to `(1,1)`, which leaves one layer of ghost (dual) cells and sets the physical origin in the lower left corner of the grid of interior dual cells.

Another optional parameter, `weights`, sets the weight of each point in the regularization. This would generally be set with, say, the differential arc length for regularization of data on a curve. It can be a vector (of the same length as x and y) or a scalar if uniform. It defaults to 1.0.

The optional Boolean parameter `filter` can be set to `true` if it is desired to apply filtering (see Goza et al, J Comput Phys 2016) to the grid data before interpolating. This is generally only used in the context of preconditioning the solution for forces on the immersed points.

If the optional Boolean parameter `issymmetric` is set to `true`, then the regularization and interpolation are constructed to be transposes of each other. Note that this option overrides any supplied weights. The default of this parameter is `false`.

The resulting operator can be used in either direction, regularization and interpolation, with the first argument representing the *target* (the entity to regularize/interpolate to), and the second argument the *source* (the entity to regularize/interpolate from). The regularization does not use the filtering option.

# Example

In the example below, we set up a 12 x 12 grid. Using the default value for `I0` and setting `dx = 0.1`, the physical dimensions of the non-ghost part of the grid are 1.0 x 1.0. Three points are set up in the interior, and a vector field is assigned to them, with the x component of each of them set to 1.0. These data are regularized to a field of primal edges on the grid, using the Roma DDF kernel.

```jldoctest
julia> x = [0.25,0.75,0.25]; y = [0.75,0.25,0.25];

julia> X = VectorData(x,y);

julia> q = Edges(Primal,(12,12));

julia> dx = 0.1;

julia> H = Regularize(x,y,dx;ddftype=Roma)
Regularization/interpolation operator with non-filtered interpolation
  DDF type CartesianGrids.Roma
  3 points in grid with cell area 0.01

julia> f = VectorData(X);

julia> fill!(f.u,1.0);

julia> H(q,f)
Edges{Primal,12,12,Float64} data
u (in grid orientation)
11×12 Array{Float64,2}:
 0.0  0.0  0.0       0.0     0.0      …  0.0       0.0     0.0      0.0  0.0
 0.0  0.0  0.0       0.0     0.0         0.0       0.0     0.0      0.0  0.0
 0.0  0.0  8.33333  33.3333  8.33333     0.0       0.0     0.0      0.0  0.0
 0.0  0.0  8.33333  33.3333  8.33333     0.0       0.0     0.0      0.0  0.0
 0.0  0.0  0.0       0.0     0.0         0.0       0.0     0.0      0.0  0.0
 0.0  0.0  0.0       0.0     0.0      …  0.0       0.0     0.0      0.0  0.0
 0.0  0.0  0.0       0.0     0.0         0.0       0.0     0.0      0.0  0.0
 0.0  0.0  8.33333  33.3333  8.33333     8.33333  33.3333  8.33333  0.0  0.0
 0.0  0.0  8.33333  33.3333  8.33333     8.33333  33.3333  8.33333  0.0  0.0
 0.0  0.0  0.0       0.0     0.0         0.0       0.0     0.0      0.0  0.0
 0.0  0.0  0.0       0.0     0.0      …  0.0       0.0     0.0      0.0  0.0
v (in grid orientation)
12×11 Array{Float64,2}:
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
```
