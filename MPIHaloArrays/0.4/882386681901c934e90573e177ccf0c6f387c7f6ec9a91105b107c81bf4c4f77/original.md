```
CartesianTopology(comm::MPI.Comm, periodicity::Bool; canreorder = false)
```

Create CartesianTopology only with the vector of boundary periodicity given. This finds the optimal sub-domain ordering for the user.
