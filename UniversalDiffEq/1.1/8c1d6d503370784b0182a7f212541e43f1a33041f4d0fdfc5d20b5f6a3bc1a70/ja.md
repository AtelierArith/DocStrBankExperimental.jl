```
plot_forecast(UDE::BayesianUDE, test_data::DataFrame)
```

モデルの予測を`test_data`の範囲にわたってプロットし、テストデータの値、中央値の予測、および`ci`%の下限および上限信頼区間を含みます。
