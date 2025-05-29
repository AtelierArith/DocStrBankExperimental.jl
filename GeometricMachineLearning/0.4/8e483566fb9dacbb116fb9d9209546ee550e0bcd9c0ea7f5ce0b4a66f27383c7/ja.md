```
DataLoader(data::QPT)
```

$$
(q, p)
$$

データに基づいて`DataLoader`のインスタンスを作成します。

# 実装

この場合、`DataLoader`のフィールド`input_dim`は$q$次元と$p$次元の合計として解釈されます。すなわち、$q$と$p$が両方とも$\mathbb{R}^n$上で進化する場合、`input_dim`は$2n$になります。

これに加えて、入力は`Array`であるかのように同様に扱われます。すなわち、すべてが内部的にテンソルに変換されます。例えば、[`DataLoader{::AbstractArray{<:Number, 3}}`](@ref)を参照してください。
