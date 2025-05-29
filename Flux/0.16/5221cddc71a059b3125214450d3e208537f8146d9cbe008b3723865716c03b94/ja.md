```
WeightNorm(layer::L, which::Symbol = :weight; dims = -1)
```

`layer`内の`which`で指定されたパラメータに重み正規化を適用します。

$$
w = g \frac{\mathbf{v}}{\lVert \mathbf{v} \rVert}
$$

重みテンソルの大きさをその方向から切り離します。デフォルトでは、正規化は出力チャネルに沿って`dim=-1`（`dims=ndims(w)`と同等）で適用されます。

### 例

```jldoctest
julia> c = Conv((3,), 1 => 2);

julia> wc = WeightNorm(c, :weight)
WeightNorm(
  Conv((3,), 1 => 2),                   # 8 parameters
  3×1×1 Array{Float32,...},             # 3 parameters
  :weight,
  3,
)                   # Total: 3 arrays, 11 parameters, 276 bytes.

julia> x = ones(Float32, 12, 1, 1);

julia> c(x) ≈ wc(x) # forward pass is the same as with the original layer
true
```

# 参考文献

Salimans & Kingma, *Weight Normalization* (2016) [https://arxiv.org/abs/1602.07868](https://arxiv.org/abs/1602.07868)
