アルファサブガウシアン (aSG) ランダム数を生成します。

実装は https://github.com/ahmd-mahm/alpha-SGNm/blob/master/asgn.m に基づいています。

参考文献: A. Mahmood と M. Chitre, "Generating random variates for stable sub-Gaussian processes with memory", Signal Processing, Volume 131, Pages 271-279, 2017. (https://doi.org/10.1016/j.sigpro.2016.08.016.)

# 引数

  * `α`: aSGN(m) プロセスに関連する特性指数。これはスカラー入力であり、`collect(1.1:0.01:1.98)` の範囲内にある必要があります。
  * `R`: aSGN(m) プロセスにおける隣接する `m+1` サンプルの共分散行列。`R` の次元は `m+1` と等しく、対称トポリッツ行列である必要があります。`R` の最大許容サイズは `10x10` です。
  * `n`: 必要なサンプル数

# 例

```jldoctest
julia> x = rand(AlphaSubGaussian(n=1000))
```
