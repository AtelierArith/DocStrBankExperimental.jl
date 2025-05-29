```
init_T2(VAR::Int, T::Int)
init_T2{tp}(data::AbstractArray{tp,2})
```

`t2_out`オブジェクトを`T2!`のために、変数の数`VAR`と観測/時間ステップ`T`のいずれか、または二次元の`data`行列（時間 * 変数）で初期化します。
