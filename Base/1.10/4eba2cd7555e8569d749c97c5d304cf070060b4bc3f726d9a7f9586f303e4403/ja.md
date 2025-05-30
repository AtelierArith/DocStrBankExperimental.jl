```
timedwait(testcb, timeout::Real; pollint::Real=0.1)
```

`testcb()`が`true`を返すか、`timeout`秒が経過するまで待機します。どちらか早い方が優先されます。テスト関数は毎`pollint`秒ごとにポーリングされます。`pollint`の最小値は0.001秒、つまり1ミリ秒です。

`:ok`または`:timed_out`を返します。
