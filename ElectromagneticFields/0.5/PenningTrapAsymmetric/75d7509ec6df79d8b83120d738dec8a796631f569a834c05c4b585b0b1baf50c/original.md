Penning trap with asymmetric magnetic field in (x,y,z) coordinates. Based on Yanyan Shi, Yajuan Sun, Yulei Wang, Jian Liu, Study of adaptive symplectic methods for       simulating charged particle dynamics, Journal of Computational Dynamics 6, 429-448, 2019.

The covariant components of the vector potential are given by

$$
A (x,y,z) = B_0 / 2 \, ( -y , x-z/6, y / 6)^T + B_1 / 2 \, (z^2 - y^2, z^2 - x^2, y^2 - x^2)^T,
$$

resulting in the magnetic field with covariant components

$$
B (x,y,z) = B_0 \, ( 1/3, 0, 1)^T + B_1 \, ( y-z, x+z, y-x )^T ,
$$

and the electrostatic potential given by

$$
\varphi (x,y,z) = E_0 \, ( x^2 / 2 + y^2 / 2 - z^2) ,
$$

resulting in the electric field with covariant components

$$
E (x,y,z) = E_0 \, ( x, y, - 2 z)^T .
$$

Parameters:

  * `B₀`: B-field strength
  * `Bₚ`: B-field perturbation strength
  * `E₀`: E-field strength
