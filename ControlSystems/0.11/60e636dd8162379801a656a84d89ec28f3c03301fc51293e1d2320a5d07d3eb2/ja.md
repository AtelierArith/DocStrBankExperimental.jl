```
rlocusplot(P::LTISystem, K)
```

SISO LTISystem P の根軌跡を計算してプロットします。負帰還ループとフィードバックゲイン `K` を持ちます。`K` が提供されていない場合、range(1e-6,stop=500,length=10000) が使用されます。ユーザーが `OrdinaryDiffEq.jl` をインストールしてロードしている場合（`using OrdinaryDiffEq`）、`rlocusplot` は適応ステップサイズアルゴリズムを使用して `K` の値を選択します。スカラー `Kmax` を第二引数として指定することもできます。
