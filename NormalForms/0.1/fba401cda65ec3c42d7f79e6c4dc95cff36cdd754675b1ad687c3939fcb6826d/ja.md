```
snf(M::AbstractMatrix{<:Integer}) -> Smith{eltype(M),M}
```

整数行列のスミス標準形を計算し、元の行列のコピーを返します。
