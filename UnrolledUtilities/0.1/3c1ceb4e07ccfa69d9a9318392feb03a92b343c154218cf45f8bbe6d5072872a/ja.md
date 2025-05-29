```
StaticOneTo(N)
```

`Base.OneTo(N)`の遅延かつ静的サイズの類似物です。

このイテレータは1から`N`までの整数のみを格納できるため、その`output_type_for_promotion`は`NoOutputType()`です。`unrolled_take`のための効率的なメソッドが提供されていますが、他のアンローリング関数は`StaticOneTo`を出力型として使用することはできません。
