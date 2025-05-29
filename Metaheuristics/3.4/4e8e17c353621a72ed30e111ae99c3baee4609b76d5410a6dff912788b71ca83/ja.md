```
MixedInteger(algorithm; information = Information(), options = Options())
```

`algorithm`が混合整数問題を処理できるようにラッパーを作成します。`MixedInteger`が使用されると、目的関数は対応する探索空間の値を持つ辞書を受け取ります。

# 例

```julia

# 目的関数
f(solution) = sum(solution[:integer]) * (1 .- sum(solution[:continuous])^2 )

# 探索空間
integer_space = BoxConstrainedSpace(-10ones(Int, 6), 10ones(Int, 6))
continuous_space = BoxConstrainedSpace(-ones(3), ones(3))
# 混合空間を形成するために空間を混合
mixed_space = MixedSpace(:integer => integer_space, :continuous => continuous_space)

# 混合整数変数を処理するためにECAをラップ
mip_eca = MixedInteger(ECA(N = 100), options = Options(seed = 1))

result = optimize(f, mixed_space, mip_eca)

# 結果の最小化者（ベクトル）を辞書に変換
solution = Metaheuristics.vec_to_dict(minimizer(result), mixed_space)
display(solution)
```

**出力**

```julia
Dict{Symbol, Vector} with 2 entries:
  :continuous => [-1.0, -1.0, -1.0]
  :integer    => [10, 10, 10, 10, 10, 10]
```
