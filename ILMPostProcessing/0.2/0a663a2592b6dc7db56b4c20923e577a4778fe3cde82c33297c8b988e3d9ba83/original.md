```
Trajectories
```

Type returned by trajectory calculations, containing a set of one or more trajectories. For an instance `traj` of this type, the trajectory time array can be returned with `traj.t`. The number of trajectories is returned by `traj.np`. Any trajectory contained in the set can be obtained with `traj[p]`, where `p` must be `0 < p <= traj.np`. 
