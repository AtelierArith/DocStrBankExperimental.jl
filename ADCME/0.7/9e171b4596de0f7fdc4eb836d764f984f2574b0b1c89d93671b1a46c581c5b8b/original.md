```
function RBF2D(xc::Union{PyObject, Array{Float64, 1}}, yc::Union{PyObject, Array{Float64, 1}}; 
    c::Union{PyObject, Array{Float64, 1}, Missing} = missing, 
    eps::Union{PyObject, Array{Float64, 1}, Real, Missing} = missing,
    d::Union{PyObject, Array{Float64, 1}} = zeros(0), 
    kind::Int64 = 0)
```

Constructs a radial basis function representation on a 2D domain

$$
f(x, y) = \sum_{i=1}^N c_i \phi(r; \epsilon_i) + d_0 + d_1 x + d_2 y
$$

Here `d` can be either 0, 1 (only $d_0$ is present), or 3 ($d_0$, $d_1$, and $d_2$ are all present).

`kind` determines the type of radial basis functions 

  * 0:Gaussian

$$
\phi(r; \epsilon) = e^{-(\epsilon r)^2}
$$

  * 1:Multiquadric

$$
\phi(r; \epsilon) = \sqrt{1+(\epsilon r)^2}
$$

  * 2:Inverse quadratic

$$
\phi(r; \epsilon) = \frac{1}{1+(\epsilon r)^2}
$$

  * 3:Inverse multiquadric

$$
\phi(r; \epsilon) = \frac{1}{\sqrt{1+(\epsilon r)^2}}
$$

Returns a callable struct, i.e. to evaluates the function at locations $(x, y)$ (`x` and `y` are both vectors), run 

```julia
rbf(x, y)
```
