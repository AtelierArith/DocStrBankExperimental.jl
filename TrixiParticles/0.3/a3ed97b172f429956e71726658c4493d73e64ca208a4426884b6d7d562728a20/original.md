```
LinearContactModel(; normal_stiffness)
```

Linear spring-dashpot contact model ([Cundall1979](@cite)).

This model calculates the normal contact force between two objects based on a linear spring law for the elastic component and a linear viscous damping law for the dissipative component. The total normal force $F_n$ is given by

$$
F_n = k_n \delta + \gamma_d v_{\text{rel,n}},
$$

where $k_n$ is the normal stiffness, $\delta$ is the overlap between the objects, $v_{\text{rel,n}}$ is the normal component of the relative velocity, and $\gamma_d$ is the damping coefficient.

The damping coefficient $\gamma_d$ is calculated based on the critical damping coefficient $\gamma_c$ and a user-provided damping ratio $C_{\text{damp}}$:

$$
\gamma_d = C_{\text{damp}} \gamma_c,
$$

where the critical damping for this linear system is

$$
\gamma_c = 2 \sqrt{m^* k_n}
$$

and $m^*$ is the effective mass of the colliding pair.

The total force is applied along the normal direction connecting the centers of the contacting objects.

# Fields

  * `normal_stiffness::Real`: Constant spring stiffness $k_n$ for the normal direction.
