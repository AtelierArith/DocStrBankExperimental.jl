```
get_chevyshevs_up_to(N::Integer, first_kind::Bool = true)
```

最初の N 個のチェビシェフ多項式を `UnivariateFunction` のベクターとして返します。最初の 20 個の多項式は、速度のためにバイナリにプリコンパイルされています。それ以上が必要な場合は、実行時に計算されます。

これらは、第一種または第二種の多項式列のいずれかから取得できます。

### 入力

  * `N` - いくつのチェビシェフ多項式が必要ですか。
  * `first_kind` - Bool。true の場合は第一種多項式を取得します。false の場合は第二種を取得します。

### 戻り値

  * 各多項式の `UnivariateFunction` の `Vector`。
