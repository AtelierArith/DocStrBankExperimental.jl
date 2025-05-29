```
write_vtk(name, assembly::Assembly, [state::AssemblyState, ]λ::Number,
    eigenstate::AssemblyState; scaling=1.0, mode_scaling=1.0, cycles=1,
    steps=100)
```

Write a series of files corresponding to the elastic motion of the `assembly` about the deformed state encoded in `state` defined by the eigenvalue `λ` and the eigenvector encoded in `eigenstate` over the time period specified by `time`.

The steady-state deflections can be scaled with `scaling` and the eigenmode deflections can be scaled using `mode_scaling`.

The current time is encoded in the metadata tag "time"
