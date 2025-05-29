```
randomwalk!(agent, model::ABM{<:ContinuousSpace} [, r];
    [polar=Uniform(-π,π), azimuthal=Arccos(-1,1)]
)
```

Re-orient and move `agent` for a distance `r` in a random direction respecting space boundary conditions. By default `r = norm(agent.vel)`.

The `ContinuousSpace` version is slightly different than the grid space. Here, the agent's velocity is updated by the random vector generated for the random walk. 

Uniform/isotropic random walks are supported in any number of dimensions while an angles distribution can be specified for 2D and 3D random walks. In this case, the velocity vector is rotated using random angles given by  the distributions for polar (2D and 3D) and azimuthal (3D only) angles, and  scaled to have measure `r`. After the re-orientation the agent is moved for  `r` in the new direction.

Anything that supports `rand` can be used as an angle distribution instead.  This can be useful to create correlated random walks.
