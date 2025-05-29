Approximate the integral of `f`, given quadrature `nodes` and `weights`

##### Arguments

  * `f::Function`: A callable function that is to be approximated over the domain spanned by `nodes`.
  * `nodes::Array`: Quadrature nodes
  * `weights::Array`: Quadrature nodes
  * `args...(Void)`: additional positional arguments to pass to `f`
  * `;kwargs...(Void)`: additional keyword arguments to pass to `f`

##### Returns

  * `out::Float64` : The scalar that approximates integral of `f` on the hypercube formed by `[a, b]`
