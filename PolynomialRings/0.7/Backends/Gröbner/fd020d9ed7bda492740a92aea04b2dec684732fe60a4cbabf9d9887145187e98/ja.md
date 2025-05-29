```
factors = lift(polynomials, y)
```

`factors`の行ベクトルを返します。`factors * polynomials`が`y`に等しい場合、または`y`が`polynomials`によって生成されたイデアルにない場合は`nothing`を返します。

これは`gröbner_transformation`を使用して計算されます。詳細についてはそちらを参照してください。

注意: 同じ`polynomials`のセットに対して多くのリフトを計算する必要がある場合は、`gröbner_transformation`を自分で使用することが有益です。これにより、最も計算集約的な部分を再実行することを避けることができます。
