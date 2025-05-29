```
trisolve(a::Union{PyObject, Array{Float64,1}},b::Union{PyObject, Array{Float64,1}},
    c::Union{PyObject, Array{Float64,1}},d::Union{PyObject, Array{Float64,1}})
```

トリディアゴナル行列線形システムを解きます。方程式は次のようになります

$$
a_i x_{i-1} + b_i x_i + c_i x_{i+1} = d_i
$$

行列形式では、

$$
\begin{bmatrix}
b_1 & c_1 & &0 \\ 
a_2 & b_2 & c_2 & \\ 
   & a_3 & b_3 & &\\ 
   &     &     & & c_{n-1}\\ 
0 & & &a_n & b_n  
\end{bmatrix}\begin{bmatrix}
x_1\\
x_2\\
\vdots \\
x_n 
\end{bmatrix} = \begin{bmatrix}
d_1\\
d_2\\
\vdots\\
d_n\end{bmatrix}
$$
