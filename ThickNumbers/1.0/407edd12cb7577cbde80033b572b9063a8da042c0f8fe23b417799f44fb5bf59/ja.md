```
midrad(::Type{TN}, mid, rad) where TN<:ThickNumber
```

中点 `mid` と半径 `rad` から `TN` を構築します。

# インターフェース要件

もし

```julia
x = midrad(TN, mid, rad)
```

がエラーを投げずに成功し、`rad >= 0` の場合、次のことが要求されます。

```julia
typeof(x) <: TN
rad(x) >= rad && rad(x) ≈ rad
```

もし `rad < 0` の場合、次のことが要求されます。

```julia
typeof(x) <: TN
isempty(x)
```
