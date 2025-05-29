```
VecJac(f, u, [p, t]; fu = nothing, autodiff = AutoFiniteDiff())
```

SciMLOperators.FunctionOperatorを返し、ベクトル-ヤコビ行列の積`(df/du)ᵀ * v`を計算します。

!!! note
    インプレースの`f`を持つ非正方行列のヤコビ行列の場合、`fu`を指定する必要があります。さもなければ、`VecJac`は正方行列のヤコビ行列を仮定します。


```julia
L = VecJac(f, u)

L * v         # = (df/du)ᵀ * v
mul!(w, L, v) # = (df/du)ᵀ * v

L(v, p, t; VJP_input = w)    # = (df/du)ᵀ * v
L(x, v, p, t; VJP_input = w) # = (df/du)ᵀ * v
```

## `f`の許可された関数シグネチャ

アウトオブプレイス関数の場合:

```julia
f(u, p, t)  # t !== nothing
f(u, p)     # p !== nothing
f(u)        # その他
```

インプレース関数の場合:

```julia
f(du, u, p, t)  # t !== nothing
f(du, u, p)     # p !== nothing
f(du, u)        # その他
```
