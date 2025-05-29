```
ProductManifold{𝔽,TM<:Tuple} <: AbstractManifold{𝔽}
```

積多様体 $M_1 × M_2 × …  × M_n$ とその積幾何。

# コンストラクタ

```
ProductManifold(M_1, M_2, ..., M_n)
```

積多様体 $M_1 × M_2 × … × M_n$ を生成します。あるいは、同じ多様体は `×` 演算子を使用して構築することもできます: `M_1 × M_2 × M_3`。
