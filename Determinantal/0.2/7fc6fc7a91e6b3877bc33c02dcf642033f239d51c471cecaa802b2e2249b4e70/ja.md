```
 sample(L::ProjectionEnsemble;nsamples=1)
```

プロジェクションDPPからサンプルを取得します。nsamples > 1の場合、プロセスからのnsamplesの実現のベクトルを返します。

nがmよりもはるかに大きい場合、通常のサンプラーの代わりに最適化された受け入れ/拒否サンプラーが呼び出されます。さらに、nsamples > 1の場合、レバレッジスコアが事前に計算されます。

最適化されたA/Rサンプラーについては、Barthelme, S, Tremblay, N, Amblard, P-O, (2022) A Faster Sampler for Discrete Determinantal Point Processesで説明されています。

```@example
    Z = randn(150,10) #ランダム特徴行列
    Pp = ProjectionEnsemble(Z)
    sample(Pp) #長さ10のベクトルを出力するはずです
    sample(Pp,nsamples=5) #5つの実現のベクトルを出力するはずです
```
