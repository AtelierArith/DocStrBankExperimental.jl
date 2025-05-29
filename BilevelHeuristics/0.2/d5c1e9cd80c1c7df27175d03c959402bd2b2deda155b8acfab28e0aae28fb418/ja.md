```
SABO(;N, K, η_max, δ1, δ2, ε1, ε2, λ, t_reevaluate)
```

二層最適化のためのサロゲートアルゴリズム。

## パラメータ

  * `N` 上位レベルの個体数
  * `K` センターを生成するための解の数。
  * `η_max` ステップサイズ
  * `δ1`, `δ2`, `ε1` `ε2` 擬似実行可能解を避けるための条件のパラメータ。
  * `λ` サロゲートモデルのパラメータ。
  * `t_reevaluate` 下位レベルが再評価されるイテレーションの数を示す。

## 使用法

上位レベルの問題: `F(x,y)` で `x` が上位レベルのベクトル。

```julia-repl
julia> F(x, y) = sum(x.^2) + sum(y.^2)
F (generic function with 1 method)

julia> bounds_ul = [-ones(5) ones(5)];

```

下位レベルの問題: `f(x, y)` で `y` が下位レベルのベクトル。

```julia-repl
julia> f(x, y) = sum((x - y).^2) + y[1]^2
f (generic function with 1 method)

julia> bounds_ll = [-ones(5) ones(5)];

```

近似解。

```julia-repl
julia> using Metaheuristics

julia> res = optimize(F, f, bounds_ul, bounds_ll, SABO(options_ul=Options(iterations=12)))
+=========== RESULT ==========+
  iteration: 12
    minimum: 
          F: 0.00472028
          f: 0.000641749
  minimizer: 
          x: [-0.03582594991950816, 0.018051141584692676, -0.030154879329873152, -0.017337812299467736, 0.004710839249040477]
          y: [-0.017912974972476316, 0.018051141514328663, -0.030154879385452187, -0.017337812317661405, 0.004710839272021738]
    F calls: 372
    f calls: 513936
    Message: Stopped due completed iterations. 
 total time: 19.0654 s
+============================+

julia> x, y = minimizer(res);

julia> x
5-element Vector{Float64}:
 -0.03582594991950816
  0.018051141584692676
 -0.030154879329873152
 -0.017337812299467736
  0.004710839249040477

julia> y
5-element Vector{Float64}:
 -0.017912974972476316
  0.018051141514328663
 -0.030154879385452187
 -0.017337812317661405
  0.004710839272021738

julia> Fmin, fmin = minimum(res)
(0.004720277765002139, 0.0006417493438175533)
```

## 引用

> Mejía-de-Dios, J. A., & Mezura-Montes, E. (2020年6月). 二層最適化のためのサロゲート支援メタヒューリスティック. 2020年遺伝的および進化的計算会議の議事録において (pp. 629-635).

