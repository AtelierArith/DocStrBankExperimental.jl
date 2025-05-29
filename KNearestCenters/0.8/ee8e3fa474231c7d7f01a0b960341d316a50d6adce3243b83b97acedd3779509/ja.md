```
transform(nc::Knc, kernel::Function, X, normalize!::Function=softmax!)
```

コレクションのオブジェクトを `nc` の各センターによって定義されたベクトル空間にマッピングします。`kernel` 関数は、各 $u \in X$ と `nc` の各センターとの類似性を測定するために使用されます。正規化関数は各ベクトルに適用されます（属性の分布を知る必要がある正規化方法は、`transform` の出力に適用できます）。
