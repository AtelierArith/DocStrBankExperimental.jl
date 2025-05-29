```
BCA(;N, n, K, η_max, resize_population)
```

バイレベルセンターアルゴリズムは、2つのネストされたECAを使用します。

## パラメータ

  * `N` 上位レベルの個体数
  * `n` 下位レベルの個体数。
  * `K` センターを生成するための解の数。
  * `η_max` ステップサイズ。

## 使用法

上位レベルの問題: `F(x,y)` で `x` が上位レベルのベクトルです。

```julia-repl
julia> F(x, y) = sum(x.^2) + sum(y.^2)
F (generic function with 1 method)

julia> bounds_ul = [-ones(5) ones(5)];

```

下位レベルの問題: `f(x, y)` で `y` が下位レベルのベクトルです。

```julia-repl
julia> f(x, y) = sum((x - y).^2) + y[1]^2
f (generic function with 1 method)

julia> bounds_ll = [-ones(5) ones(5)];

```

近似解。

```julia-repl
julia> res = optimize(F, f, bounds_ul, bounds_ll, BCA())
+=========== RESULT ==========+
  iteration: 108
    minimum: 
          F: 2.7438e-09
          f: 3.94874e-11
  minimizer: 
          x: [-8.80414308649828e-6, 2.1574853199308744e-5, -1.5550602817418899e-6, 1.9314104453973864e-5, 2.1709393089480435e-5]
          y: [-4.907639660543081e-6, 2.173986368018122e-5, -1.8133242873785074e-6, 1.9658451600356374e-5, 2.1624363965042988e-5]
    F calls: 2503
    f calls: 6272518
    Message: Stopped due UL function evaluations limitations. 
 total time: 14.8592 s
+============================+

julia> x, y = minimizer(res);

julia> x
5-element Vector{Float64}:
 -8.80414308649828e-6
  2.1574853199308744e-5
 -1.5550602817418899e-6
  1.9314104453973864e-5
  2.1709393089480435e-5

julia> y
5-element Vector{Float64}:
 -4.907639660543081e-6
  2.173986368018122e-5
 -1.8133242873785074e-6
  1.9658451600356374e-5
  2.1624363965042988e-5

julia> Fmin, fmin = minimum(res)
(2.7438003987697017e-9, 3.9487399650845625e-11)
```

## 引用

> Mejía-de-Dios, J. A., & Mezura-Montes, E. (2018, November). A physics-inspired algorithm for bilevel optimization. In 2018 IEEE International Autumn Meeting on Power, Electronics and Computing (ROPEC) (pp. 1-6). IEEE.

