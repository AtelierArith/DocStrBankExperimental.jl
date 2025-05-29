```
monthlyagg(A::ClimArray, f = mean; mday = 15) -> B
```

新しい配列を作成し、時間情報を関数 `f` を使用して月ごとに集約します。新しい配列の日付は常に日番号 `mday` になります。
