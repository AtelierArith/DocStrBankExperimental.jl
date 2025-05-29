```
DebugStoppingCriterion <: DebugAction
```

print the Reason provided by the stopping criterion. Usually this should be empty, unless the algorithm stops.

# Fields

  * `prefix=""`: format to print the output
  * `io=stdout`: default stream to print the debug to.

# Constructor

DebugStoppingCriterion(prefix = ""; io::IO=stdout)
