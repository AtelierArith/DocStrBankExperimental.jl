```
CartesianTopology(comm::MPI.Comm, dims, periodicity; canreorder = false)
```

Create a CartesianTopology type that holds neighbor information, current rank, etc.

# Arguments

  * `dims`: Vector or Tuple setting the dimensions of the domain in each direction, e.g. (4,3) means a total of 12 procs, with 4 in x and 3 in y
  * `periodicity`: Vector or Tuple of bools to set if the domain is periodic along a specific dimension

# Example

```julia

# Create a topology of 4x4 with periodic boundaries in both directions
P = CartesianTopology((4,4), (true, true))
```
