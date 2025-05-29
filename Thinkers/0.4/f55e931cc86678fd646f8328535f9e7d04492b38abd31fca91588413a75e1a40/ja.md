```
getresult(thunk::Thunk)
```

`Thunk`の結果を取得します。`thunk`が再現されていない場合は`nothing`を返し、そうでなければ`Some`でラップされた結果を返します。
