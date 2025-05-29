```
dispersion(c; k = 40, kwargs...)
```

`c`の語彙の分散を`k`個の同じサイズのパーティションに分けた`BitMatrix`を取得します。結果の次元は`V(c) x k`になります。

`k`を指定する代わりに、`endpoints`のベクトルを渡すこともできます。（詳細は`partition`を参照してください。）
