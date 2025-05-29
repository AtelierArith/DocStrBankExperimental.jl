```
add_registered_to_jump(opt_model::JuMP.Model, inf_model::InfiniteModel)::Nothing
```

`inf_model`に登録されたユーザー関数を`JuMP`モデル`opt_model`に追加します。これは内部メソッドとして意図されていますが、他の最適化モデルを使用するために`InfiniteOpt`を拡張する開発者向けに提供されています。
