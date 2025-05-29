```
reload_neural_model(file)
```

`reload_neural_data` は、フィットからのパラメータ、最適化に関するいくつかの詳細（`fit` や境界ベクトルなど）、およびデータをフィルタリングした方法に関するいくつかの詳細を持ち帰ります。すべてのデータは、`load_neural_data` によって読み込まれる形式で保存されていないため、シリアライズするのが面倒すぎるので、上記のように再度読み込んで `neuralDDM` を再構築する必要がありますが、`reload_neural_data` が返すいくつかの情報（`pad` や `dt` など）を使用して、同じ方法でデータを再読み込みすることができます。

返すもの:

  * `θneural`
  * `neural_options`
  * n
  * cross
  * dt
  * delay
  * pad

参照: [`save_neural_model`](@ref)
