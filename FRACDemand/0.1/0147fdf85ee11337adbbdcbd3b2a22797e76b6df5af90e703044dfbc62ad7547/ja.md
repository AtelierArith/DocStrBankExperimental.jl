```
correlate_draws(raw_draws, data, nonlinear, cov, parameters)
```

独立した標準正規分布のサンプルが `raw_draws` に与えられ（Kの長さの行列のベクトル、サイズ n*obs×I）、完全に推定された共分散構造が `parameters` に含まれている場合（キー :σ2*var および :σcov*var1*var2）、次元間で指定された相関を示す新しいサンプルセットを返します。
