The additive coupling layer specifies an invertible function ${\bf{y}} = g({\bf{x}})$ following the specific structure (for the mapping $g: \mathbb{R}^2 \rightarrow \mathbb{R}^2$):

$$
    \begin{align}
        y_1 &= x_1 \\
        y_2 &= x_2 + f(x_1)
    \end{align}
$$

where $f(\cdot)$ denotes an arbitrary function with mapping $f: \mathbb{R} \rightarrow \mathbb{R}$. This function can be chosen arbitrarily complex. Non-linear functions (neural networks) are often chosen to model complex relationships. From the definition of the model, invertibility can be easily achieved as

$$
    \begin{align}
        x_1 &= y_1 \\
        x_2 &= y_2 - f(y_1)
    \end{align}
$$

The current implementation only allows for the mapping $g: \mathbb{R}^2 \rightarrow \mathbb{R}^2$, although this layer can be generalized for arbitrary input dimensions.

`AdditiveCouplingLayer(f <: AbstractCouplingFlow)` creates the layer structure with function `f`.

### Example

```julia
f = PlanarFlow()
layer = AdditiveCouplingLayer(f)
```

This layer structure has been introduced in:

Dinh, Laurent, David Krueger, and Yoshua Bengio. "Nice: Non-linear independent components estimation." *arXiv preprint* arXiv:1410.8516 (2014).
