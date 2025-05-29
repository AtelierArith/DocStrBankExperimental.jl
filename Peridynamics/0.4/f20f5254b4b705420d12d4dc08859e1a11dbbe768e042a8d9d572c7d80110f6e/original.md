```
enable_mpi_progress_bars!()
```

Helper function to enable progress bars with MPI simulations on a personal computer. After this function is called, progress bars are beeing shown with MPI simulations like with multithreading simulations. This behavior can be reset to default with [`reset_mpi_progress_bars!`](@ref).

!!! warning "Progress bars and output files"
    Progress bars are by default disabled with MPI simulations, because they can really mess up with the output files produced by a HPC system. Therefore, a warning is shown as a reminder to reset this behaviour before submitting a job to a cluster!

