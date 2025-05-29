```
SummationByPartsOperators
```

[SummationByPartsOperators.jl](https://github.com/ranocha/SummationByPartsOperators.jl) is a Julia library of summation-by-parts (SBP) operators, which are discrete derivative operators developed to get provably stable semidiscretizations, paying special attention to boundary conditions. Discretizations included in this framework are finite difference, Fourier pseudospectral, continuous Galerkin, and discontinuous Galerkin methods. The main aim of [SummationByPartsOperators.jl](https://github.com/ranocha/SummationByPartsOperators.jl) is to be useful for researchers and students to learn the basic concepts by providing a unified framework of all of these seemingly different discretizations. At the same time, the implementation is optimized to achieve good performance without sacrificing flexibility.

Check out the [documentation](https://ranocha.github.io/SummationByPartsOperators.jl/stable) for further information. Some noticeable functions to start with are [`derivative_operator`](@ref), [`legendre_derivative_operator`](@ref), [`periodic_derivative_operator`](@ref), [`fourier_derivative_operator`](@ref), [`dissipation_operator`](@ref), and [`grid`](@ref).

If you use this package for your research, please cite it using

```bibtex
@article{ranocha2021sbp,
  title={{SummationByPartsOperators.jl}: {A} {J}ulia library of provably stable
         semidiscretization techniques with mimetic properties},
  author={Ranocha, Hendrik},
  journal={Journal of Open Source Software},
  year={2021},
  month={08},
  doi={10.21105/joss.03454},
  volume={6},
  number={64},
  pages={3454},
  publisher={The Open Journal},
  url={https://github.com/ranocha/SummationByPartsOperators.jl}
}
```
