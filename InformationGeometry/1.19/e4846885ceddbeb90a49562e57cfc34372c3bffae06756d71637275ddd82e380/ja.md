```
MLEuncert(DM::AbstractDataModel, mle::AbstractVector=MLE(DM), F::AbstractMatrix=FisherMetric(DM, mle))
```

返されるのは、パラメータの不確実性が逆フィッシャー計量の対角線を介して近似される `Measurements.Measurement` 型のベクトルです。つまり、記載された不確実性は、MLEの周りの真のパラメータ不確実性の線形対称近似です。
