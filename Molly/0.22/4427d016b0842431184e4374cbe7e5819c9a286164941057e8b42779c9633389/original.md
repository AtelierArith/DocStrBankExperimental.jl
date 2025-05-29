```
apply_coupling!(system, coupling, simulator, neighbors=nothing, step_n=0;
                n_threads=Threads.nthreads(), rng=Random.default_rng())
```

Apply a coupler to modify a simulation.

Returns whether the coupling has invalidated the currently stored forces, for example by changing the coordinates. This information is useful for some simulators. If `coupling` is a tuple or named tuple then each coupler will be applied in turn. Custom couplers should implement this function.
