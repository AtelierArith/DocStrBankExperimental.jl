```
Apollo(opt::AdamW = AdamW(), r::Function = dim -> ceil(Int, sqrt(dim)); u = 100, sort_dims = true)
Apollo(η::Real, args...; kw...)
Apollo(arg, rank::Int; kw...)
Apollo(η::Real, rank::Int; kw...)
```

Zhu et al.によるApolloオプティマイザ (https://arxiv.org/abs/2412.05270)。低ランク部分空間でモーメントを追跡し、最小限の追加メモリ使用でAdamのような動作を目指します。最初の引数はAdamWオプティマイザ、または学習率（その学習率でデフォルトのAdamWオプティマイザを使用します）です。2番目の引数はランク、または重み行列（またはテンソル）の2次元目（またはすべての次元 > 1 の積）からランクを計算する関数です。
