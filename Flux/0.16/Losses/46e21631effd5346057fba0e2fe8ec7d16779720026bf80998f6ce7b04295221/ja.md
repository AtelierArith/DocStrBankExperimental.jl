```
mse(ŷ, y; agg = mean)
```

平均二乗誤差に対応する損失を返します：

```
agg((ŷ .- y) .^ 2)
```

参照： [`mae`](@ref), [`msle`](@ref), [`crossentropy`](@ref).

# 例

```jldoctest
julia> y_model = [1.1, 1.9, 3.1];

julia> y_true = 1:3;

julia> Flux.mse(y_model, y_true)
0.010000000000000018
```
