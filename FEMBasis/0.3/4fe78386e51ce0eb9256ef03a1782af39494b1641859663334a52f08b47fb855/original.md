Evaluate basis, gradient and so on for some point `xi`.

# Examples

```jldoctest

b = BasisInfo(Quad4)
X = Vec.([(0.0,0.0), (1.0,0.0), (1.0,1.0), (0.0,1.0)])
xi = Vec(0.0, 0.0)
eval_basis!(b, X, xi)

# output

BasisInfo{Quad4,2,Float64,4}([0.25, 0.25, 0.25, 0.25], Tensors.Tensor{1,2,Float64,2}[[-0.25, -0.25], [0.25, -0.25], [0.25, 0.25], [-0.25, 0.25]], Tensors.Tensor{1,2,Float64,2}[[-0.5, -0.5], [0.5, -0.5], [0.5, 0.5], [-0.5, 0.5]], [0.5 0.0; 0.0 0.5], [2.0 -0.0; -0.0 2.0], 0.25, Quad4)

```
