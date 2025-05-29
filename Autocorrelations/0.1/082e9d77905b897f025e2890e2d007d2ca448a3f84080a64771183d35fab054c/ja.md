```
acf!(r, x, lags; demean=false, normalize=false)
```

`x`の`lags`における自己相関をインプレースで評価し、出力を`r`に格納します。`acf`を参照してください。このインプレースバージョンでは、`lags`を指定する必要があり、`length(r)==length(lags)`でなければなりません。
