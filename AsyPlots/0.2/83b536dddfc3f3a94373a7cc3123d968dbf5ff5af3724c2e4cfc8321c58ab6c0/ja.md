```
plot(x,y;kwargs...)
plot(y;kwargs...)
```

`x` と `y` の値が `x` と `y` によって与えられるパスのグラフを返します。

`x` のデフォルトは `0:length(y)-1` です。 `kwargs` は、適切に線を表す `Path2D` オブジェクトまたは含まれる `Plot2D` に適用されます。

```
plot(xs::Vector{<:Vector{<:Real}},
     ys::Vector{<:Vector{<:Real}};
     kwargs...)
```

同じ図に複数の線グラフ

```
plot(x,y,z;kwargs...)
plot(z::Array{<:Real,2};kwargs...)
```

`x`、`y`、および `z` の値 `x`、`y`、および `z` を持つ表面のグラフ

`x` のデフォルトは `[i-1 for i=1:size(z,1),j=1:size(z,2)]` で、`y` のデフォルトは `[j-1 for i=1:size(z,1),j=1:size(z,2)]` です。

# 例

```julia-repl
plot(cumsum(randn(100)))
plot(rand(5,5))
```
