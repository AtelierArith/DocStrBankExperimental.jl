```
MajoranaReg{T} <: AbstractRegister{2}
MajoranaReg(state::AbstractMatrix{T<:Real})
```

FLO回路を通過する際のマヨラナ演算子の「状態」を保持するレジスタで、`2n×2n` 行列として表現されます。

# 警告

`MajoranaReg` コンストラクタは `state` 行列を初期化しません。初期状態を生成するには、`FLOYao.zero_state` または `FLOYao.product_state` を使用することをお勧めします。
