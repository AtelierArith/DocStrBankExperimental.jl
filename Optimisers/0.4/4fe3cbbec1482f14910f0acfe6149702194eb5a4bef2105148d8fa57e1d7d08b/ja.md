```
RMSProp(η = 0.001, ρ = 0.9, ϵ = 1e-8; centred = false)
RMSProp(; [eta, rho, epsilon, centred])
```

[RMPSProp](https://www.cs.toronto.edu/~tijmen/csc321/slides/lecture_slides_lec6.pdf)アルゴリズムを使用するオプティマイザ。再帰ネットワークにとってはしばしば良い選択です。学習率以外のパラメータは一般的に調整する必要はありません。

[Centered RMSProp](http://arxiv.org/abs/1308.08500)は、勾配の二次モーメントではなく、分散の推定値で勾配を正規化する変種です。

# パラメータ

  * 学習率（`η == eta`）：重みを更新する前に勾配が割引かれる量。
  * モーメンタム（`ρ == rho`）：勾配降下の主要な方向への加速を制御し、実際には振動を抑制します。
  * マシンイプシロン（`ϵ == epsilon`）：ゼロ除算を防ぐための定数（デフォルトを変更する必要はありません）
  * キーワード`centred`（または`centered`）：アルゴリズムの中心化された変種を使用するかどうかを示します。
