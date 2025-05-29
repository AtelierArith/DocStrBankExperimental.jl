Gillespie's Direct method. `ConstantRateJump` rates and affects are stored via `FunctionWrappers`, which is more performant than `Direct` for very large numbers of `ConstantRateJump`s. However, for such large numbers of jump different classes of aggregators are usually much more performant (i.e. `SortingDirect`, `DirectCR`, `RSSA` or `RSSACR`).

Daniel T. Gillespie, A general method for numerically simulating the stochastic time evolution of coupled chemical reactions, Journal of Computational Physics, 22 (4), 403–434 (1976). doi:10.1016/0021-9991(76)90041-3.
