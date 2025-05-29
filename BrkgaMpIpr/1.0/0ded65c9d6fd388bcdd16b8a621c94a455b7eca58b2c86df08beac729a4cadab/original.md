```
@enum PathRelinkingResult
```

Specifies the result type/status of path relink procedure:

  * `TOO_HOMOGENEOUS`: the chromosomes among the populations are too homogeneous                    and the path relink will not generate improveded                    solutions.
  * `NO_IMPROVEMENT`: path relink was done but no improveded solution was found.
  * `ELITE_IMPROVEMENT`: an improved solution among the elite set was found,                      but the best solution was not improved.
  * `BEST_IMPROVEMENT`: the best solution was improved.
