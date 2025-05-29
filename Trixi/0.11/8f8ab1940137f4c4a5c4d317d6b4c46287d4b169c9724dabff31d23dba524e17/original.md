```
AMRCallback(semi, controller [,adaptor=AdaptorAMR(semi)];
            interval,
            adapt_initial_condition=true,
            adapt_initial_condition_only_refine=true,
            dynamic_load_balancing=true)
```

Performs adaptive mesh refinement (AMR) every `interval` time steps for a given semidiscretization `semi` using the chosen `controller`.
