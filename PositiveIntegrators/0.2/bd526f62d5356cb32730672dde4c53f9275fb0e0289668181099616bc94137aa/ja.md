```
MPE([linsolve = ..., small_constant = ...])
```

生産-破壊システムのための一次修正パタンカール-オイラーアルゴリズム。この一段階の手法は、一次精度を持ち、無条件に正の値を保持し、線形的に暗黙的です。

この手法は、保守的な生産-破壊システムのためにBurchardらによって導入されました。非保守的な生産-破壊システムの場合は、単純な拡張を使用します。

$$
u_i^{n+1} = u_i^n + Δt \sum_{j, j≠i} \biggl(p_{ij}^n \frac{u_j^{n+1}}{u_j^n}-d_{ij}^n \frac{u_i^{n+1}}{u_i^n}\biggr) + {\Delta}t p_{ii}^n - Δt d_{ii}^n\frac{u_i^{n+1}}{u_i^n}
$$

,

ここで、$p_{ij}^n = p_{ij}(t^n,\mathbf u^n)$および$d_{ij}^n = d_{ij}(t^n,\mathbf u^n)$です。

修正パタンカール-オイラー法は、[`PDSProblem`](@ref)または[`ConservativePDSProblem`](@ref)の特別な構造を必要とします。

オプションで、キーワード引数`linsolve`として[LinearSolve.jl](https://github.com/SciML/LinearSolve.jl)からアルゴリズムを渡すことで使用する線形ソルバーを選択できます。また、ゼロでの除算を避けるために、すべてのパタンカール重みの分母に追加されるパラメータ`small_constant`を選択することもできます。値を明示的に渡すことができますが、そうでない場合は`small_constant`は使用される浮動小数点型の`floatmin`に設定されます。

現在の実装は、固定時間ステップのみをサポートしています。

## 参考文献

  * Hans Burchard, Eric Deleersnijder, and Andreas Meister. "A high-order conservative Patankar-type discretisation for stiff systems of production-destruction equations." Applied Numerical Mathematics 47.1 (2003): 1-30. [DOI: 10.1016/S0168-9274(03)00101-6](https://doi.org/10.1016/S0168-9274(03)00101-6)
