```
eer(tar, non)
```

等誤差率（EER）の単純な近似を計算します。これは、ROCと直線 `y=x` の交点、すなわち偽陽性率と偽陰性率がほぼ等しくなるエラー率です。

EERのより一貫した解釈と実装を考慮する場合は、Equal Error Rate - Convex Hull計算である `eerch()` をご利用ください。
