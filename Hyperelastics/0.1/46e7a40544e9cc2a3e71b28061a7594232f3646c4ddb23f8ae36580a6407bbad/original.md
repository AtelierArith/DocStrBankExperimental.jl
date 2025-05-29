```julia
DataDrivenAverageChainBehavior(data; fchain)

```

Model:

  * Adapted from the code provided in the article's supplementary material

Parameters:

  * None

Fields:

  * `data`: A Uniaxial Hyperelastic Test
  * `fchain(λch, pch)`: A constructor for an approximation with the form f(x, y) => f̂(x) = y

> Amores VJ, Benítez JM, Montáns FJ. Average-chain behavior of isotropic incompressible polymers obtained from macroscopic experimental data. A simple structure-based WYPiWYG model in Julia language. Advances in Engineering Software. 2019 Apr 1;130:41-57.


> Amores VJ, Benítez JM, Montáns FJ. Data-driven, structure-based hyperelastic manifolds: A macro-micro-macro approach to reverse-engineer the chain behavior and perform efficient simulations of polymers. Computers & Structures. 2020 Apr 15;231:106209.

