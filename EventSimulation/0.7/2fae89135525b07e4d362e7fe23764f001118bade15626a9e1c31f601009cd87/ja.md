```
interrupt!(s, a)
```

最初の `Action` `a` の出現は、イベントキュー内でノーオプに置き換えられます。この方法では、この操作でヒープを修正する必要がなく、迅速です。`a` がキュー内で見つかった場合は `true` を返し、そうでない場合は `false` を返します。
