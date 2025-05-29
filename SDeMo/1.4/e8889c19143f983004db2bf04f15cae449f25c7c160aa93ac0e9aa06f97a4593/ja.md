```
StatsAPI.predict(sdm::SDM, X; threshold = true)
```

これは主な予測関数で、SDMと特徴の行列を入力として受け取ります。唯一のキーワード引数は`threshold`で、予測が生の値として返されるか、バイナリ値として返されるかを決定します（デフォルトは`true`です）。
