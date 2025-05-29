```
build_optimizer_model!(model::InfiniteModel, key::Val{ext_key_name};
                       [kwargs...])
```

`model`に格納された最適化モデルを構築し、`Model.ext`フィールドにデータ構造に適切にデータをマッピングするキーが含まれる通常のJuMPモデルとして扱えるようにします。キー引数は`Val{ext_key_name}`に型付けされるべきです。また、現在の最適化モデルを空にするために[`clear_optimizer_model_build!`](@ref)を使用する必要があります。最終的には、[`set_optimizer_model`](@ref)を呼び出して構築した最適化モデルを`model`に挿入し、[`set_optimizer_model_ready`](@ref)を使用して最適化モデルのステータスを更新する必要があります。
