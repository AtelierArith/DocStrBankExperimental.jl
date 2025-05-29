```
isprime(n::Integer) -> Bool
```

Returns for values in the range of an INT64 variable:  `true` if `n` is prime, and `false` otherwise         for bigger values: `true` if `n` is probably prime, and `false` otherwise (false-positive rate = 0.25^reps with reps=25 –> considered safe)

```
More detailed:
for even numbers: returns deterministic and correct results
for values in the range of an  INT64 variable: returns deterministic and correct results (by Lookup-tables, trial-division, Miller-Rabin, Lucas-Test)
for bigger values: returns probabilistic resultsfrom GNU Multiple Precision Arithmetic Library
```

```julia
julia> isprime(3)
true
```
