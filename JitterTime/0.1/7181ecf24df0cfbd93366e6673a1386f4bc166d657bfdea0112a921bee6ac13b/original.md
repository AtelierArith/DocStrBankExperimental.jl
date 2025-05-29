```
calcDynamics!(N::JTSystem)
```

Calculate the total system dynamics for the JitterTime system `N`. 

Assuming the state of the total system (including all subsystems) to be x.

The continuous time evolution follows the equation

```
dx(t) = N.Ac x(t)dt + dvc(t)
```

where `vc` is continuous white noise with intensity `N.Rc`.

The discrete-event evolution (when executing system `S`) follows the equation `x+(t_k) = S.Ad x(t_k) + vd(t_k)``where vd is white Gaussian noise with variance`S.Rd`.
