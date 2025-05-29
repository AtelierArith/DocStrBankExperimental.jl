```julia
HookStiffnessOperator2D(
    μ,
    λ;
    name,
    AT,
    regions,
    ϵ,
    store
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}

```

ビリニア形式 a(u,v) = (C ϵ(u), ϵ(v)) のコンストラクタで、ここで C は等方性媒体のための2D剛性テンソルで、ボイト記法で表されます。すなわち、ℂ ϵ(u) = 2 μ ϵ(u) + λ tr(ϵ(u)) で、ラメパラメータ μ と λ に対してです。

```
ボイト記法では ℂ は 3 x 3 行列です
ℂ = [c11,c12,  0
     c12,c11,  0
       0,  0,c33]

ここで c33 = μ, c12 = λ および c11 = 2*c33 + c12 です。
```

注: ϵ は勾配の対称部分です（ボイト記法で）。
