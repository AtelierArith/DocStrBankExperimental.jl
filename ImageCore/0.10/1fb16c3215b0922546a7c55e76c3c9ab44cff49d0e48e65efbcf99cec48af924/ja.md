```
scaleminmax(min, max) -> f
scaleminmax(T, min, max) -> f
```

値が `min` 以下の場合は 0 に、`max` 以上の場合は 1 にマッピングし、その間は線形スケールを使用する関数 `f` を返します。`min` と `max` は実数値である必要があります。

オプションで戻り値の型 `T` を指定できます。`T` が色彩（例：RGB）の場合、スケーリングは各色チャネルに適用されます。

# 例

## 例 1

```julia
julia> f = scaleminmax(-10, 10)
(::#9) (generic function with 1 method)

julia> f(10)
1.0

julia> f(-10)
0.0

julia> f(5)
0.75
```

## 例 2

```julia
julia> c = RGB(255.0,128.0,0.0)
RGB{Float64}(255.0,128.0,0.0)

julia> f = scaleminmax(RGB, 0, 255)
(::#13) (generic function with 1 method)

julia> f(c)
RGB{Float64}(1.0,0.5019607843137255,0.0)
```

参照: [`takemap`](@ref).
