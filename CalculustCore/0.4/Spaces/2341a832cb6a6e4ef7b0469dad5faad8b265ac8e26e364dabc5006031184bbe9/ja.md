```
hessianOp(V::AbstractSpace{T, D}) where{T, D} ->
```

$$
[∂x1∂x1 ... ∂x1∂xD,         ...  ∂xD∂x1 ... ∂xD∂xD ]
$$

ヘッセ行列演算子: ∇²

`D × D` の演算子の `Matrix` を返し、その `[ij]` 番目のエントリは、関数からその第二偏導関数への変換を `[ij]` 番目の方向で表します。
