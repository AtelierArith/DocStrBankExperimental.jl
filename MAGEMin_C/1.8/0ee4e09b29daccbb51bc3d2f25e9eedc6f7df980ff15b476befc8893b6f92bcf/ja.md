```
out = point_wise_minimization(P::Number,T::Number, data::MAGEMin_Data)
```

与えられた圧力 `P` と温度 `T` に対して、MAGEMinデータベース `MAGEMin_Data` に指定されたデータ（ここで組成も指定されている）に対して点ごとの最適化を実行します。
