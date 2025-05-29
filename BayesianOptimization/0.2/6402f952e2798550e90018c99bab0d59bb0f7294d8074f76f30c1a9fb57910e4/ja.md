```
BOpt(func, model, acquisition, modeloptimizer, lowerbounds, upperbounds;
          sense = Max, maxiterations = 10^4, maxduration = Inf,
          acquisitionoptions = NamedTuple(), repetitions = 1,
          verbosity = Progress,
          initializer_iterations = 5*length(lowerbounds),
          initializer = ScaledSobolIterator(lowerbounds, upperbounds,
                                            initializer_iterations))
```
