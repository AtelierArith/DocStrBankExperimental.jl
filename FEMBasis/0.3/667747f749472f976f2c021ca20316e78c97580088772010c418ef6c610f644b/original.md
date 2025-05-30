```
grad!(bi, gradu, u)
```

Evalute gradient ∂u/∂X and store result to matrix `gradu`. It is assumed that `eval_basis!` has been already run to `bi` so it already contains all necessary matrices evaluated with some `X` and `xi`.

# Example

First setup and evaluate basis using `eval_basis!`:

```jldoctest ex1
B = BasisInfo(Quad4)
X = Vec.([(0.0,0.0), (1.0,0.0), (1.0,1.0), (0.0,1.0)])
xi = Vec(0.0, 0.0)
eval_basis!(B, X, xi)

# output

BasisInfo{Quad4,2,Float64}([0.25, 0.25, 0.25, 0.25], Tensors.Tensor{1,2,Float64,2}[[-0.25, -0.25], [0.25, -0.25], [0.25, 0.25], [-0.25, 0.25]], Tensors.Tensor{1,2,Float64,2}[[0.0, 0.0], [0.0, 0.0], [0.0, 0.0], [-0.5, 0.5]], [0.5 0.0; 0.0 0.5], [2.0 -0.0; -0.0 2.0], 0.25)

```

Next, calculate gradient of `u`:

```jldoctest ex1
u = Vec.([(0.0, 0.0), (1.0, -1.0), (2.0, 3.0), (0.0, 0.0)])
grad(B, u)

# output

2×2 Tensors.Tensor{2,2,Float64,4}:
 1.5  0.5
 1.0  2.0

```
