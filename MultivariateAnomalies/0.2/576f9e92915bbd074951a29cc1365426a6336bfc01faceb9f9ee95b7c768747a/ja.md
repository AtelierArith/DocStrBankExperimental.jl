```
init_UNIV(T::Int, VAR::Int)
init_UNIV{tp}(data::AbstractArray{tp, 2})
```

`UNIV!()` で使用する `univ_out` オブジェクトを、時間ステップ/観測の数 `T` と変数 `VAR` で初期化するか、`data` 行列の観測 * 変数で初期化します。
