```
MCCGA(;N, maxsamples)
```

### Parameters:

  * `N` population size. Default is 100.
  * `maxsamples` maximum number of samples. Default is 10000.

### Description

MCCGA method implements the Machine-coded genetic algorithms for real valued optimization problems.  The algorithm is based on the concept of a compact genetic algorithm but with a machine-coded representation  using IEEE-754 floating point encoding standard. In the first stage of the algorithm, `maxsamples` number  of samples are generated within the range of function domain. This process is required to obtain a vector of probabilities for each single bit of the IEEE-754 representation. In classical CGAs, the initial vector  of probabilities is generated using the constant probability of 0.5 whereas in MCCGA, the probability of ith bit having a value of 1 depends on the function domain. The second step performs a CGA search but with IEEE-754 bits again. Since  CGA does not use a population of solutions but a single vector of probabilities, the parameter `N` does not really mean  number of solutions. Instead, it means the amount of mutation in each iteration, e.g. 1/N.  In the last stage, a local search is performed for fine-tuning. In this implementation, Hooke & Jeeves  direct search algorithm is used.

### References

  * Moser, Irene. "Hooke-Jeeves Revisited." 2009 IEEE Congress on Evolutionary Computation. IEEE, 2009.
  * Harik, G. R., Lobo, F. G., & Goldberg, D. E. (1999). The compact genetic algorithm. IEEE transactions on evolutionary computation, 3(4), 287-297.
  * Satman, M. H. & Akadal, E. (2020). Machine Coded Compact Genetic Algorithms for Real Parameter Optimization Problems . Alphanumeric Journal , 8 (1) , 43-58 . DOI: 10.17093/alphanumeric.576919
  * Mehmet Hakan Satman, Emre Akadal, Makine Kodlu Hibrit Kompakt Genetik Algoritmalar Optimizasyon Yöntemi, Patent, TR, 2022/01, 2018-GE-510239

### Example

```jldoctest

julia> f, bounds, solutions = Metaheuristics.TestProblems.rastrigin();

julia> result = optimize(f, bounds, MCCGA())

+=========== RESULT ==========+
  iteration: 42833
    minimum: 0
  minimizer: [-5.677669786379456e-17, 2.7942451898022582e-39, -3.60925916059986e-33, -6.609510861086017e-34, 2.998586759675011e-32, -1.8825832500775007e-38, -3.0729484147585938e-31, 1.7675578057632446e-38, 5.127944874215823e-16, 1.9623770480857484e-19]
    f calls: 86404
 total time: 3.2839 s
+============================+
```

### Explicit Example

```jldoctest

julia> using Metaheuristics                                                                                         
                                                              
julia> f(x::Vector{Float64})::Float64 = (x[1]-pi)^2 + (x[2]-exp(1))^2                                                                                
                                                              
julia> bounds = [ -500.0  -500.0;                                    
                   500.0  500.0]                                      

julia> result = Metaheuristics.optimize(f, bounds, MCCGA())

+=========== RESULT ==========+
  iteration: 2974
    minimum: 1.80997e-09
  minimizer: [3.1416284249228976, 2.7183048585824263]
    f calls: 6012
 total time: 1.5233 s
stop reason: Other stopping criteria.
+============================+
```
