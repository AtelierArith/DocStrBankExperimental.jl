```
WeightedValidation(weighting, folding; lambda=1.0, loss=Dict())
```

サンプルが `weighting` メソッドで重み付けされ、`folding` メソッドでフォールドに分割される誤差推定方法です。重みは `[0,1]` の範囲で `lambda` 乗されます。オプションで、いくつかの変数に対して `LossFunctions.jl` からの `loss` 関数を含む辞書を指定できます。

## 参考文献

  * Sugiyama et al. 2006. [重要度重み付き交差検証による共変量シフト](https://link.springer.com/chapter/10.1007/11861898_36)
  * Sugiyama et al. 2007. [重要度重み付き交差検証による共変量シフト適応](http://www.jmlr.org/papers/volume8/sugiyama07a/sugiyama07a.pdf)
