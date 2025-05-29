```
 mb03vy!(n::Integer, p::Integer, ilo::Integer, ihi::Integer, A::Array{Float64, 3}, tau::AbstractMatrix{Float64}) -> info::Int64
```

実数直交行列 `Q_1`, `Q_2`, ..., `Q_p` を生成します。これらは `mb03vd!` によって `A_1`, `A_2`, ..., `A_p` に返される `ihi-ilo` 次の基本反射体の積として定義されます：

```
 Q_j = H_j(ilo) H_j(ilo+1) . . . H_j(ihi-1).
```

3次元配列 `A` と `tau` には、使用される基本反射体に関する情報が含まれています。結果として得られる `Q_1`, `Q_2`, ..., `Q_p` は `A_1`, `A_2`, ..., `A_p` を上書きします。

詳細については、`MB03VY` の SLICOT ドキュメントを参照してください。
