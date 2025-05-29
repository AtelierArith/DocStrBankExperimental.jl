```
scalingtest(fd::Type{<:MarginalScalingModel}, data::IDFdata;
    tag_out::String, q::Integer)
```

モデル fd がデータを考慮して拒否される可能性があるかどうかを判断するためのテスト手順を実行します。テストの p 値を返します。d_out は検証セットに入れるべき期間です。デフォルトでは、データ内の最小の期間に設定されます。q は、p 値の Zolotarev 近似を使用する際に計算する固有値の数です。
