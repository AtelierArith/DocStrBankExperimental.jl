```
Spline(y::Array{T,1}, kind::Symbol = :open)::Spline where {T<:Number}
```

`Spline(vals,kind)` は `vals` の値に基づいて三次スプラインを返します。結果として得られるスプライン `S` は、`S(1)==y[1]`、`S(2)==y[2]`、そして `S(n)==y[n]` までの性質を持ち、ここで `n` は `y` の長さです。

  * `kind` が `:open` の場合、端点での二次導関数はゼロになります。（これがデフォルトです。）
  * `kind` が `:closed` の場合、`S(n+1)==S(1)` となる周期関数を補間していると仮定します。
