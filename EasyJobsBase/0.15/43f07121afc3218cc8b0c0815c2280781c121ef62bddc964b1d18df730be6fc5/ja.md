```
getresult(job::AbstractJob)
```

`job`の実行結果を取得します。

結果は`Some`型でラップされています。`something`を使用してその値を取得します。もし`nothing`であれば、`job`は完了していません。
