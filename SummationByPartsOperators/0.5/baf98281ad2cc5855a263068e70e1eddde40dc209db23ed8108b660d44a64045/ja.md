```
SummationByPartsOperators
```

[SummationByPartsOperators.jl](https://github.com/ranocha/SummationByPartsOperators.jl) は、境界条件に特に注意を払って、証明可能に安定した半離散化を得るために開発された離散微分演算子である部分和演算子（SBP）を提供するJuliaライブラリです。このフレームワークに含まれる離散化には、有限差分法、フーリエ擬似スペクトル法、連続ガレルキン法、および不連続ガレルキン法が含まれます。[SummationByPartsOperators.jl](https://github.com/ranocha/SummationByPartsOperators.jl) の主な目的は、これらの一見異なる離散化のすべてを統一されたフレームワークで提供することにより、研究者や学生が基本的な概念を学ぶのに役立つことです。同時に、実装は柔軟性を犠牲にすることなく良好なパフォーマンスを達成するように最適化されています。

さらなる情報については、[documentation](https://ranocha.github.io/SummationByPartsOperators.jl/stable) をご覧ください。最初に試すべき注目すべき関数には、[`derivative_operator`](@ref)、[`legendre_derivative_operator`](@ref)、[`periodic_derivative_operator`](@ref)、[`fourier_derivative_operator`](@ref)、[`dissipation_operator`](@ref)、および[`grid`](@ref)があります。

このパッケージを研究に使用する場合は、以下のように引用してください。

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
