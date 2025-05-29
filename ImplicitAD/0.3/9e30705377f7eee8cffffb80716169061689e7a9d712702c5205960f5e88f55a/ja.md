```
provide_rule(func, x, p=(); mode="ffd", jacobian=nothing, jvp=nothing, vjp=nothing)
```

ADに依存せず部分的なルールを提供します。ADが利用できない場合や独自のルールを提供する場合、または混合モードを使用する場合などです。

# 引数

  * `func::function`, `x::vector{float}`, `p::tuple`: 形式が y = func(x, p) の関数で、x は変数、p は固定パラメータです。
  * `mode::string`:

      * "ffd": 前方有限差分
      * "cfd": 中央有限差分
      * "cs": 複素ステップ
      * "jacobian": 独自のヤコビ行列を提供（ヤコビ行列関数を参照）
      * "vp": ヤコビ行列ベクトル積とベクトルヤコビ行列積を提供（jvp と vjp を参照）
  * `jacobian::function`: mode="jacobian" の場合のみ使用されます。 J = jacobian(x, p) は J*ij = dy*i / dx_j を提供します。
  * `jvp::function`: mode="vp" かつ前方モードの場合のみ使用されます。 ydot = jvp(x, p, v) はヤコビ行列ベクトル積 J*v を提供します。
  * `vjp::function`: mode="vp" かつ逆モードの場合のみ使用されます。 xbar = vjp(x, p, v) はベクトルヤコビ行列積 v'*J を提供します。
