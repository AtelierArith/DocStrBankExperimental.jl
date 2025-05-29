```
plot_forecast(UDE::BayesianUDE, T::Int)
```

モデルの予測を、最後の観測からT時間先までプロットします。中央値の予測と、`ci`%の下限および上限の信頼区間も含まれます。
