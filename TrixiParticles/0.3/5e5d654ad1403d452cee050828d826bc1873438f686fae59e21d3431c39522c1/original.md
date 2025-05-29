```
HertzContactModel(; elastic_modulus, poissons_ratio)
```

Non-linear contact model based on Hertzian contact theory ([DiRenzo2004](@cite)).

This model calculates the normal contact force between two spherical particles (or a particle and a boundary represented by an equivalent sphere) based on their material properties and the overlap $\delta$. The elastic part of the force is given by:

$$
F_{\text{elastic}} = \frac{4}{3} E^* \sqrt{R^*} \delta^{3/2},
$$

where $E^*$ is the effective Young's modulus and $R^*$ is the effective radius.

The effective Young's modulus $E^*$ is calculated from the Young's moduli $E_a, E_b$ and Poisson's ratios $\nu_a, \nu_b$ of the two contacting bodies:

$$
E^* = \left( \frac{1 - \nu_a^2}{E_a} + \frac{1 - \nu_b^2}{E_b} \right)^{-1}.
$$

The effective radius $R^*$ is calculated from the radii of the two particles $R_a$ and  $R_b$:

$$
R^* = \left( \frac{1}{R_a} + \frac{1}{R_b} \right)^{-1} = \frac{R_a R_b}{R_a + R_b}.
$$

For particle-wall interactions, $R_b \to \infty$, so $R^* = R_a$.

The implementation also includes a damping force based on the approach described in [DiRenzo2004](@cite), proportional to the normal component of the relative velocity $v_{\text{rel,n}}$:

$$
F_{\text{damping}} = C_{\text{damp}} \gamma_c v_{\text{rel,n}},
$$

where $C_{\text{damp}}$ is the user-provided damping coefficient (damping ratio), and $\gamma_c$ is a non-linear critical damping coefficient:

$$
\gamma_c = 2 \sqrt{m^* K_{\text{nonlin}}}
$$

with $m^*$ being the effective mass and $K_{\text{nonlin}}$ being a non-linear stiffness term related to the current state:

$$
K_{\text{nonlin}} = \frac{F_{\text{elastic}}}{\delta} = \frac{4}{3} E^* \sqrt{R^* \delta}.
$$

The total normal force is $F_n = F_{\text{elastic}} + F_{\text{damping}}$.

# Fields

  * `elastic_modulus::Float64`: Material Young's modulus $E$.
  * `poissons_ratio::Float64`: Material Poisson's ratio $\nu$.
