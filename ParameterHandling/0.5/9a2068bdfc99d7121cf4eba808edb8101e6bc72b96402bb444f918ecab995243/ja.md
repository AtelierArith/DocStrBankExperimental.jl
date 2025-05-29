```
deferred(f, args...)
```

`deferred`の`value`は`f(value(args)...)`です。これにより、`args`の値を例えば`AbstractParameter`にすることが可能になり、したがって、`f`が`AbstractParameters`について何も知らなくても、それらに制約を強制することができます。

複雑なオブジェクトを構築する際に、再帰的に`deferred`を使用することが役立つ場合があります。
