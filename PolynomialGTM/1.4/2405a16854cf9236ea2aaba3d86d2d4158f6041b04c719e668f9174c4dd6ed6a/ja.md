```julia
GTM(; stm, name)

```

NASAの汎用輸送モデルは、（特定の飛行条件の近くで）多項式モデルとして近似できます。ここで、`GTM`は、GTMの縦の飛行力学に対する公開されている多項式近似を提供する`ModelingToolkit.ODESystem`です。

# 拡張ヘルプ

## 初期条件

デフォルトの初期条件は1つのトリム条件です。これらの多項式近似された力学に対する2つのトリム条件は以下に示されています。

```julia
trim₁ = [[29.6, deg2rad(9), 0.0, deg2rad(9)],   [deg2rad(0.68), 12.7]]
trim₂ = [[25.0, deg2rad(18), 0.0, deg2rad(18)], [deg2rad(-7.2), 59]]
```

## 使用法

```julia
model = GTM()
```

## 参考文献:

  * [Chakraborty et al](https://www.sciencedirect.com/science/article/abs/pii/S0967066110002595)
  * [Joe Carpinelli](https://github.com/cadojo/Replicated-ROA-Analysis)
