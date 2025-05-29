```
localgeary(x, W)
```

空間自己相関のローカル・ギアリ検定を計算します。

# オプション引数

  * `permutations=9999`: ランダム化検定のための置換の数。
  * `rng=default_rng()`: ランダム化検定のための乱数生成器。
  * `corrected=true`: スケーリング因子を $n-1$ で割る代わりに $n$ で割ります。
  * `categories=:positivenegative`: 観測値を正のまたは負の空間自己相関に割り当てるか、または `:moran` 散布図と組み合わせて使用します。
