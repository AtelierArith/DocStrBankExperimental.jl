```
QPois(results)
```

INGARCHモデルの準準ポアソン推定のためのアドオン関数。

  * `results`: 推定結果（INGARCHのみ）

# 例

```julia-repl
QPois(results)
```

この関数は、ポアソン分布を用いたINGARCHフィットの推定結果を使用し、[Christou and Fokianos (2013)](https://doi.org/10.1111/jtsa.12050)に従って過分散パラメータを推定します。この関数は、過分散パラメータの推定を含む入力の変更されたバージョンを出力します。これにより、分布は「NegativeBinomial」に変更されます。
