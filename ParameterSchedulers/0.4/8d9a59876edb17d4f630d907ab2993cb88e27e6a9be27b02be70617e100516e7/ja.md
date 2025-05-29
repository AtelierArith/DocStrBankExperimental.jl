```
OneCycle(nsteps, maxval;
         startval = maxval / 25,
         endval = maxval / 1f5,
         percent_start = 0.25)
```

`nsteps` ステップで `startval` から `maxval` までウォームアップし、次に `endval` まで戻る1サイクルのコサインスケジュールを作成します（詳細は [Super-Convergence: Very Fast Training of Neural Networks Using Large Learning Rates](https://arxiv.org/abs/1708.07120) を参照）。
