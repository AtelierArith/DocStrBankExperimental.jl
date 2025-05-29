```
roc(pred_scores, real_scores)
```

返されるのはベクトルのタプル (FPR, TPR) であり、ここで FPR は「偽陽性率」、TPR は「真陽性率」です。`real_scores` の各スコアは、スコアが正の場合に正と解釈されます。ROC曲線をプロットするには、Plots.jlを使用して `plot(FPR, TPR, linetype=:steppost)` とします。
