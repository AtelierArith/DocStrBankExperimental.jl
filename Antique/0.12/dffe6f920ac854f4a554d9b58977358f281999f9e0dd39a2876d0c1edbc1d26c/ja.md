`ψ(model::InfinitePotentialWell3D, x; n::Vector{Int}=[1,1,1])`

波動関数は、一次元の箱の波動関数の積として表現できます。

$$
\begin{aligned}
  \psi_{n_x,n_y,n_z}(x,y,z)
  &=     \psi_{n_x}(x)
  \times \psi_{n_y}(y)
  \times \psi_{n_z}(z) \\
  &=     \sqrt{\frac{2}{L_x}} \sin \frac{n_x \pi x}{L_x}
  \times \sqrt{\frac{2}{L_y}} \sin \frac{n_y \pi y}{L_y}
  \times \sqrt{\frac{2}{L_z}} \sin \frac{n_z \pi z}{L_z}
\end{aligned}
$$
