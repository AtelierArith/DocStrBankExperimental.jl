```
MPITopology{N}
```

Describes an N-dimensional Cartesian MPI decomposition topology.

---

```
MPITopology(comm::MPI.Comm, pdims::Dims{N})
```

Create N-dimensional MPI topology information.

The `pdims` tuple specifies the number of MPI processes to put in every dimension of the topology. The product of its values must be equal to the number of processes in communicator `comm`.

# Example

Divide 2D topology into 4×2 blocks:

```julia
comm = MPI.COMM_WORLD
@assert MPI.Comm_size(comm) == 8
topology = MPITopology(comm, (4, 2))
```

---

```
MPITopology(comm::MPI.Comm, Val(N))
```

Convenient `MPITopology` constructor defining an `N`-dimensional decomposition of data among all MPI processes in communicator.

The number of divisions along each of the `N` dimensions is automatically determined by a call to [`MPI.Dims_create`](https://juliaparallel.org/MPI.jl/stable/reference/topology/#MPI.Dims_create).

# Example

Create 2D decomposition grid:

```julia
comm = MPI.COMM_WORLD
topology = MPITopology(comm, Val(2))
```

---

```
MPITopology{N}(comm_cart::MPI.Comm)
```

Create topology information from MPI communicator with Cartesian topology (typically constructed using [`MPI.Cart_create`](https://juliaparallel.org/MPI.jl/stable/reference/topology/#MPI.Cart_create)). The topology must have dimension `N`.

# Example

Divide 2D topology into 4×2 blocks:

```julia
comm = MPI.COMM_WORLD
@assert MPI.Comm_size(comm) == 8
pdims = (4, 2)
comm_cart = MPI.Cart_create(comm, pdims)
topology = MPITopology{2}(comm_cart)
```
