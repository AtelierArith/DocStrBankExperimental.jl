```
wr(system_a, reference_b, particle_c=0)
```

Create a WignerRotation object of the right type based on provided indices. The daughter particles are numbered 1,2,3, the mother particle is 0.

  * `system_a` tells which isobar is considered, and
  * `reference_b` tell which system is used as a reference.

For `system_a` and `reference_b` the spectator notations are used, i.e. 1 for the system (2,3), 2 for the system (3,1), and 3 for the system (1,2).
