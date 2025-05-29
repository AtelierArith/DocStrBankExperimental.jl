```
EulerAcousticsCouplingCallback
```

!!! warning "Experimental code"
    This callback is experimental and may change in any future release.


A callback that couples the acoustic perturbation equations and compressible Euler equations. Must be used in conjunction with [`SemidiscretizationEulerAcoustics`](@ref). This callback manages the flow solver - which is always one time step ahead of the acoustics solver - and calculates the acoustic source term after each time step. The linearized Lamb vector is used as the source term, i.e.

$$
\mathbf{s} = -(\mathbf{\omega'} \times \bar{\mathbf{v}}
  + \bar{\mathbf{\omega}} \times \mathbf{v'}),
$$

where $\mathbf{v}$ denotes the velocity, $\mathbf{\omega}$ denotes the vorticity, the bar $\bar{(\cdot)}$ indicates time-averaged quantities (see [`AveragingCallback`](@ref)) and prime $(\cdot)'$ denotes perturbed quantities defined by $\phi' = \phi - \bar{\phi}$. Note that the perturbed quantities here are based entirely on the pure flow solution and should not be confused with the state variables of the acoustic perturbation equations.

In addition, this callback manages the time step size for both solvers and initializes the mean values of the acoustic perturbation equations using results obtained with the [`AveragingCallback`](@ref).

  * Michael Schlottke-Lakemper (2017) A direct-hybrid method for aeroacoustic analysis [DOI: 10.18154/RWTH-2017-04082](https://doi.org/10.18154/RWTH-2017-04082)
