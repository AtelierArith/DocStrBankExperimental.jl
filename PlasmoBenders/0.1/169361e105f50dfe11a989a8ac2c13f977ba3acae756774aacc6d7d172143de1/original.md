```
run_algorithm!(optimizer::PB.BendersAlgorithm; output::Bool = true, run_gc::Bool = false)
```

Optimize the graph in BendersAlgorithm by using the Benders algorithm. Keyword argument `output` indicates whether to print the upper/lower bounds and gap and each iteraiton. `run_gc` indicates whether to run the garbage collector after each iteraiton. 
