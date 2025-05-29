```
set_initial_population!(brkga_data::BrkgaData,
                        chromosomes::Array{Array{Float64, 1}, 1})
```

Set initial individuals into the poulation to work as warm-starters. Such individuals can be obtained from solutions of external procedures such as fast heuristics, other methaheuristics, or even relaxations from a mixed integer programming model that models the problem.

All given solutions are assigned to one population only. Therefore, the maximum number of solutions is the size of the populations.

# Throws

  * `ArgumentError`: if the number of given chromosomes is larger than the population size; if the sizes of the given chromosomes do not match with the required chromosome size.
