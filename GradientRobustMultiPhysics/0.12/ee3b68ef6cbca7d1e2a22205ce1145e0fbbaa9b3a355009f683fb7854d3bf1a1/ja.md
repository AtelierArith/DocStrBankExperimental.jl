```julia
HookStiffnessOperator3D(
    μ,
    λ;
    name,
    AT,
    regions,
    ϵ,
    store
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}

```

ビリニア形式 a(u,v) = (C ϵ(u), ϵ(v)) のコンストラクタで、ここで C は等方性媒体のための3D剛性テンソルで、ボイト記法で表されます。すなわち、ℂ ϵ(u) = 2 μ ϵ(u) + λ tr(ϵ(u)) で、ラメパラメータ μ と λ に対してです。

```
ボイト記法では ℂ は 6 x 6 行列です
ℂ = [c11,c12,c12,  0,  0,  0
     c12,c11,c12,  0,  0,  0
     c12,c12,c11,  0,  0,  0
       0,  0,  0,c44,  0,  0
       0,  0,  0,  0,c44,  0
       0,  0,  0,  0,  0,c44]   

ここで c44 = μ, c12 = λ および c11 = 2*c44 + c12 です。
```

注意: ϵ は勾配の対称部分です（ボイト記法で）。
