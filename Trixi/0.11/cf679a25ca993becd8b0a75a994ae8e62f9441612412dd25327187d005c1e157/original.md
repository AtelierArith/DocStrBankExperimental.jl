```
SaveSolutionCallback(; interval::Integer=0,
                       dt=nothing,
                       save_initial_solution=true,
                       save_final_solution=true,
                       output_directory="out",
                       solution_variables=cons2prim)
```

Save the current numerical solution in regular intervals. Either pass `interval` to save every `interval` time steps or pass `dt` to save in intervals of `dt` in terms of integration time by adding additional (shortened) time steps where necessary (note that this may change the solution). `solution_variables` can be any callable that converts the conservative variables at a single point to a set of solution variables. The first parameter passed to `solution_variables` will be the set of conservative variables and the second parameter is the equation struct.
