```
perform_method_pair!(scheduler, destroy, repair, sol)
```

Performs a destroy/repair method pair on given solution and returns `Results` structure.

Also updates incumbent, iteration and the method's statistics in method_stats. Furthermore checks the termination condition and eventually sets terminate in the  returned `Results` structure.
