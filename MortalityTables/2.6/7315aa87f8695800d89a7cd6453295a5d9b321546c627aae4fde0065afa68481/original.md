```
survival(mortality_vector,to_age)
survival(mortality_vector,from_age,to_age)
```

Returns the survival through attained age `to_age`. The start of the calculation is either the start of the vector, or attained*age `from*age`.`from*age`and`to*age` need to be Integers. Add a DeathDistribution as the last argument to handle floating point and non-whole ages:

```
survival(mortality_vector,to_age,::DeathDistribution)
survival(mortality_vector,from_age,to_age,::DeathDistribution)
```

If given a negative `to_age`, it will return `1.0`. Aside from simplifying the code, this makes sense as for something to exist in order to decrement in the first place, it must have existed and survived to the point of  being able to be decremented.

# Examples

```julia-repl
julia> qs = UltimateMortality([0.1,0.3,0.6,1]);
    
julia> survival(qs,0)
1.0
julia> survival(qs,1)
0.9

julia> survival(qs,1,1)
1.0
julia> survival(qs,1,2)
0.7

julia> survival(qs,0.5,Uniform())
0.95
```
