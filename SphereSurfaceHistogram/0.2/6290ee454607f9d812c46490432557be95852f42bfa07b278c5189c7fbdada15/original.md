```
partition_sphere1(dA)
```

Partitions a sphere into bins of size `dA` where number of divisions in ϕ (0..2π) is not restricted, i.e. it can be any integer.

Note that for a random `dA` this will not produce equally sized bins. (Specifically bins at z ≈ 0 will be wrong.) The algorithm relies on `partition_sphere_optim` to optimize `dA` to a value fitting on the sphere surface which happens during the creation of an `SSHBinner`.
