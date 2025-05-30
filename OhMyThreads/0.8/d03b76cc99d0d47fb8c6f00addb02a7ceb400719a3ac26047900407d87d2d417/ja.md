```
@disallow_boxed_captures expr
```

`expr`内の任意のコードに対する`@allow_boxed_captures`の効果を無効にします。

これは動的スコープの構造であるため、この効果は`expr`内の*すべての*ネストされたコードに適用されます。

`@disallow_boxed_captures`も参照してください。
