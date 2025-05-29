```
create_model(mip_solver, lp_solver, use_direct_model, use_model_names, add_bridges)
```

`JuMP.Model`を拡張してSpineOptで使用できるようにしたものです。`mip_solver`と`lp_solver`は`JuMP.Model`または`JuMP.direct_model`に渡すための「オプティマイザーファクトリー」です。`use_direct_model`は`JuMP.Model`または`JuMP.direct_model`を使用するかどうかを示す`Bool`です。`use_model_names`はモデル内の名前を使用するかどうかを示す`Bool`です。`add_bridges`はJuMPからソルバーへのブリッジをモデルに追加するかどうかを示す`Bool`です。
