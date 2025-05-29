```
BiweightScaleRMS(c=9.0, M=nothing)
```

背景RMS推定のためのロバストなバイウェイトスケール統計を使用します。

バイウェイトスケールは、バイウェイト中分散の平方根です。バイウェイト中分散は、調整定数`c`と、中央値`M`のオプションの初期推定値を使用します。

$$
ζ²_{biscl} = \frac{n ∑_{|uᵢ|<1}{(xᵢ - M)²(1 - uᵢ²)⁴}}{\left[∑_{|uᵢ|<1}{(1-uᵢ²)(1-5uᵢ²)}\right]²}
$$

$$
uᵢ = \frac{(xᵢ - M)}{c⋅\mathrm{MAD}(x)}
$$

ここで、$\mathrm{MAD}(x)$は`x`の中央値絶対偏差です。

# 例

```jldoctest
julia> data = ones(3, 5);

julia> BiweightScaleRMS()(data)
0.0

julia> BiweightScaleRMS(c=3.0)(data, dims=1)
1×5 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0
```
