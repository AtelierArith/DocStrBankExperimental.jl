```julia
reaction!(
    f,
    u,
    node,
    data,
    _::Type{ChargeTransport.OutOfEquilibrium}
)

```

Sets up the right-hand sides. Assuming a bipolar semiconductor the right-hand side for the electrostatic potential becomes   $f[ψ]  = - q ((p - N_a) - (n - N_d) ) = - q  \sum  n_\alpha  (n_\alpha - C_\alpha)$ for some doping $C_\alpha$ w.r.t. to the species $\alpha$. The right-hand sides for the charge carriers read as $f[n_\alpha] =  - z_\alpha  q (G -  R)$ for all charge carriers $n_\alpha$. The recombination includes radiative, Auger and Shockley-Read-Hall recombination. For latter recombination process the stationary simplification is implemented. The recombination is only implemented for electron and holes and assumes that the electron index is 1 and the hole index is 2.
