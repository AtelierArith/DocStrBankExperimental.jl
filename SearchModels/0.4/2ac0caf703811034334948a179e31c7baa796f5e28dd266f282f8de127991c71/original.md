```
SearchParams(;
    maxpopulation::Int = 32
    bsize::Int = 16
    mutbsize::Int = 8
    crossbsize::Int = 8
    maxiters::Int = 300
    verbose::Bool = true
)
```

reates a mutable list of search parameters, it can be changed online via `inspect_population`.

  * `maxpopulation`: the maximum number of configurations to be kept at each iteration (based on its minimum error)
  * `bsize`: number of best items to be used for mutation and crossing procedures
  * `mutbsize`: number of new configurations per iteration from a mutation procedure
  * `crossbsize`: number of new configurations per iteration from a crossing procedure
  * `maxiters`: maximum iterations of the search procedure
  * `verbose`: controls if the verbosity of the search iterations
