```
TwoUniformDependent(a, b, c, ϵ)
TwoUniformDependent(a, b, c) (デフォルト ϵ = 1e-10 のコンストラクタ)

2つの確率変数をモデル化する多変量分布で、最初の変数は U[a,b] で与えられ、2番目の変数は U[x,c] で与えられます。ここで、x は最初の分布からサンプリングされた確率変数です。

  * `a`: 最初の分布の下限
  * `b`: 最初の分布の上限
  * `c`: 2番目の分布の上限
  * `ϵ`: 各分布の下限と上限が異なることを保証するための小さな値

これは、2番目の分布の下限が最初の分布の値に依存していることを意味します。これは、動的サポートを持つ依存事前分布に対する現在のTuringの実装の制限を克服するために実装されています。詳細については、以下の問題を参照してください: [[1]](https://github.com/TuringLang/Turing.jl/issues/1558),[[2]](https://github.com/TuringLang/Turing.jl/issues/1708),[[3]](https://github.com/TuringLang/Turing.jl/issues/1270).

# 例

```

jldoctest julia> using Pioran, Distributions julia> d = TwoUniformDependent(0, 1, 2) TwoUniformDependent(0.0, 1.0, 2.0)

julia> rand(d) 2-element Array{Float64,1}:  0.123  1.234 ```
