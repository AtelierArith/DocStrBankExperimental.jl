```
read_hamiltonian(job::Job)
```

Goes through the job and will attempt to read the hamiltonian files. If it finds a colinear calculation in the job it will read the up and down hamiltonians, if the job was either nonmagnetic or noncolinear it will read only one hamiltonian file (there should be only one).
