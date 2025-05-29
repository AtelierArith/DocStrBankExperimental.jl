```
accelerations(system, neighbors=find_neighbors(sys), step_n=0; n_threads=Threads.nthreads())
```

Calculate the accelerations of all atoms in a system using the pairwise, specific and general interactions and Newton's second law of motion.
