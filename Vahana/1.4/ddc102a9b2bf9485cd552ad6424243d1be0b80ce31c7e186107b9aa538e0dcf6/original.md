```
copy_simulation(sim)
```

Create an independent copy of the simulation `sim`. Since part of the memory is allocated via MPI, you should not use deepcopy. 

Also, the copy is detached from any output or logger file so that not sim and copy tried to write to the same file(s). If these are needed, you can create these files for the copy by calling [`create_h5file!`](@ref) and/or [`create_logger!`](@ref) and assigning the results to the h5file/logging field of the returned simulation.

Returns the copy of the simulation.
