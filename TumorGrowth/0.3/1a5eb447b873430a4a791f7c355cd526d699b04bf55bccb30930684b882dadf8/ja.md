```
exponential(times, p)
```

指定された `times` に基づいて、病変成長の指数モデルに対する解析解に基づいて体積を返します。ここで `p` は `v0` と `ω` のプロパティを持ち、`v0` は時間 `times[1]` における体積であり、`log(2)/ω` は半減期です。成長には負の `ω` を、減衰には正の `ω` を使用します。

# 基本的な常微分方程式

指数モデルでは、体積 $v > 0$ は次の微分方程式に従って進化します。

$$
dv/dt = -ω v.
$$

すべてのモデルのリストについては、[`TumorGrowth`](@ref) を参照してください。
