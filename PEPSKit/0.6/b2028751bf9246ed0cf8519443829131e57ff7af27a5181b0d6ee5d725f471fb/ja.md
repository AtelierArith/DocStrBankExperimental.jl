```
correlation_length(state, env::CTMRGEnv; num_vals=2, kwargs...)
```

`state`に関連する相関長を、`env`に基づいて収束させて計算します。これは、`env`に関連する水平および垂直の転送行列のスペクトルに基づいています。さらに、（正規化された）固有値スペクトルも返されます。計算される固有値の数は`num_vals`を使用して指定でき、残りのキーワード引数は`MPSKit.transfer_spectrum`に渡されます（例：特定の対称セクターで相関長をターゲットにすることを可能にします）。
