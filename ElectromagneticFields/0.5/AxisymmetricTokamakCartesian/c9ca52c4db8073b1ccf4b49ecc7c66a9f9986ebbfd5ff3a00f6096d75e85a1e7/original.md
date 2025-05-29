Axisymmetric tokamak equilibrium in (x,y,z) coordinates with covariant components of the vector potential given by

$$
A (x,y,z) = \frac{1}{2} \frac{B_0}{q_0} \, \bigg( \frac{q_0 R_0 x z - r^2 y}{R^2} , \, \frac{q_0 R_0 y z + r^2 x}{R^2} , \, - q_0 R_0 \, \ln \bigg( \frac{R}{R_0} \bigg) \bigg)^T ,
$$

resulting in the magnetic field with covariant components

$$
B (x,y,z) = \frac{B_0}{q_0} \, \bigg( - \frac{q_0 R_0 y + x z}{R^2} , \, \frac{q_0 R_0 x - y z}{R^2} , \, \frac{R - R_0}{R} \bigg)^T ,
$$

where $R = \sqrt{ x^2 + y^2 }$ and $r = \sqrt{ (R - R_0)^2 + z^2 }$.

Parameters:

  * `R₀`: position of magnetic axis
  * `B₀`: B-field at magnetic axis
  * `q₀`: safety factor at magnetic axis
