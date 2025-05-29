```
JuMP.backend(model::InfiniteModel)
```

`backend`を拡張して、最適化モデルに関連付けられた`MathOptInterface`バックエンドを返します。最適化モデルがまだ構築されていない場合、これは空になります。

**例**

```julia-repl
julia> moi_model = backend(model);
```
