```
trend_chrt(SimTimeArray, PeriodRange::Vector{Date}; x_label="periods", quantiles=[0.05,0.5,0.95])
```

シミュレーションされた時系列を信頼区間と共に視覚化します。PeriodRangeは日付のベクトルでなければなりません（例：Datesを使用して `collect(Date(2019,1,1):Year(1):Date(2023,1,1))`）。
