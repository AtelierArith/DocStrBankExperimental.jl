```
incompatibility_robustness(
    A::Vector{Measurement{<:Number}};
    noise::String = "general",
    return_parent::Bool = false,
    verbose::Bool = false,
    solver = Hypatia.Optimizer{_solver_type(T)})
```

ベクトル `A` の測定値の不適合性ロバスト性を計算します。選択したノイズモデルに応じて、第二引数は "depolarizing" (`{tr(Aₐ)I/d}ₐ`、ここで `d` はシステムの次元)、"random" (`{I/n}ₐ`、ここで `n` は結果の数)、"probabilistic" (`{pₐI}ₐ`、ここで `p` は確率分布)、"jointly*measurable"、または "general"（デフォルト）を指定できます。`return*parent = true` の場合、親POVMを返します。

参考文献:

  * Designolle, Farkas, Kaniewski, [arXiv:1906.00448](https://arxiv.org/abs/1906.00448) （異なるノイズモデルについて）
  * Gühne et al., [arXiv:2112.06784](https://arxiv.org/abs/2112.06784) （セクション III.B.2）
