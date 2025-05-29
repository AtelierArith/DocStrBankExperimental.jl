Gillespie's Direct method. `ConstantRateJump` rates and affects are stored via `FunctionWrappers`, which is more performant than `Direct` for very large numbers of `ConstantRateJump`s. However, for such large numbers of jump different classes of aggregators are usually much more performant (i.e. `SortingDirect`, `DirectCR`, `RSSA` or `RSSACR`).

Gillespie, Daniel T. (1976). A General Method for Numerically Simulating the Stochastic Time Evolution of Coupled Chemical Reactions. Journal of Computational Physics. 22 (4): 403–434. doi:10.1016/0021-9991(76)90041-3.
