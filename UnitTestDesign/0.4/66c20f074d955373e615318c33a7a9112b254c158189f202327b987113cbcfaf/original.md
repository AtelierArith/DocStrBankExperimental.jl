```
all_tuples(parameters...; n_way, engine, disallow, seeds, wayness, Counter)
```

Given a tuple of parameters, generate all test cases that cover all `n_way` combinations of those parameters.

# Arguments

  * `engine=IPOG()`: The `engine` is `IPOG()`, `GND()` or `Excursion()`.
  * `disallow=nothing`: The disallow function is a function of the parameters that returns `true` when that combination should be forbidden.
  * `seeds=[]`: is a list of test cases that must be included among those

generated.

  * `wayness` is a dictionary that specifies subsets of parameters for which to increase the `n_way` combinations. For instance, if the combinations are two-way, and you want the third-sixth parameters to be three-way covered, use, `wayness = Dict(3 => [[3, 4, 5, 6]])`.
  * `Counter=Int`The Counter is an integer type to use for

the computation. It must be large enough to hold the integer number of the parameters.

# Examples

```julia
all_tuples([1, 2, 3], ["a", "b", "c"], [true, false]; n_way = 2)
parameters = fill(collect(1:3), 10)
all_tuples(parameters...; n_way = 4, engine = Excursion())
```
