```
Wrapper(
   default_args = Dict(
      :name => "ohe-wrapper",
      # 呼び出すトランスフォーマー。
      :transformer => OneHotEncoder(),
      # トランスフォーマーの引数。
      :transformer_args => Dict()
   )
)
```

トランスフォーマーをラップします。

`fit!` と `transform` を実装します。
