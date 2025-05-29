```julia
    SA(;
        x_initial::Vector = zeros(0),
        N::Int = 500,
        tol_fun::Real= 1e-4,
        information = Information(),
        options = Options()
    )
```

シミュレーテッドアニーリング法のパラメータ (Kirkpatrick et al., 1983)。

パラメータ:

  * x_intial: 初期解。空の場合、SAは境界内でランダムな解を生成します。
  * N: 各イテレーションあたりのテストポイントの数。
  * tol_fun: メトロポリス条件におけるテストポイントを現在のポイントとして受け入れるか拒否するための許容値。

# 例

```jldoctest
julia> f(x) = sum(x.^2)
f (generic function with 1 method)

julia> optimize(f, [-1 -1 -1; 1 1 1.0], SA())
+=========== RESULT ==========+
  iteration: 60
    minimum: 5.0787e-68
  minimizer: [-2.2522059499734615e-34, 3.816133503985569e-36, 6.934348004465088e-36]
    f calls: 29002
 total time: 0.0943 s
+============================+

julia> optimize(f, [-1 -1 -1; 1 1 1.0], SA(N = 100, x_initial = [1, 0.5, -1]))
+=========== RESULT ==========+
  iteration: 300
    minimum: 1.99651e-69
  minimizer: [4.4638292404181215e-35, -1.738939846089388e-36, -9.542441152683457e-37]
    f calls: 29802
 total time: 0.0965 s
+============================+
```
