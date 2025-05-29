```
JacVec(f, u, [p, t]; fu = nothing, autodiff = AutoForwardDiff(), tag = DeivVecTag(),
    kwargs...)
```

SciMLOperators.FunctionOperatorを返し、ジャコビアン-ベクトル積`df/du * v`を計算します。

!!! note
    インプレースの`f`を持つ非正方ジャコビアンの場合、`fu`を指定する必要があります。さもなければ、`JacVec`は正方ジャコビアンを仮定します。


```julia
L = JacVec(f, u)

L * v         # = df/du * v
mul!(w, L, v) # = df/du * v

L(v, p, t)    # = df/dw * v
L(x, v, p, t) # = df/dw * v
```

## `f`のための許可された関数シグネチャ

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
