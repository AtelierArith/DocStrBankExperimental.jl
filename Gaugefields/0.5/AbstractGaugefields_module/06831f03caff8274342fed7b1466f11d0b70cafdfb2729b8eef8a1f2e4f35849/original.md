```
Initialize_Gaugefields(NC,NDW,NN...;
    condition = "cold",mpi = false,PEs=nothing,mpiinit = nothing,verbose_level = 2,randomnumber="Random")
```

Initialize gaugefields. 2D or 4D is supported. 

### Examples

If you want to have randomely distributed gauge fields (so-called "hot start") in four dimension, just do:

```julia
U = Initialize_Gaugefields(NC,Nwing,NX,NY,NZ,NT,condition = "hot")
```

If you want to have uniform gauge fields (so-called "cold start") in four dimension, just do:

```julia
U = Initialize_Gaugefields(NC,Nwing,NX,NY,NZ,NT,condition = "cold")
```

### Return values:

  * `U`: Dim dimensional vector. Here, Dim is a dimension (Dim = 2 or 4).

### Keyword arguments:

  * `condition`: `cold`(cold start) or `hot`(hot start). The default is `cold`
  * `mpi`: Using MPI or not. The default is `false`. If you want to use MPI, you should call `using MPI`.
  * `PEs`: If `mpi = true`, we have to set `PEs = [2,2,2,2]`, which is numbers of regions for MPI process. `prod(PEs)` should be the number of total MPI processes.

### MPI

Gaugefields with using MPI is not well tested. 
