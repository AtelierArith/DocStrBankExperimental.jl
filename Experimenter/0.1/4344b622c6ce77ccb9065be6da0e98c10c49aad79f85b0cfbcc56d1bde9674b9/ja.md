```
get_global_store()
```

指定された関数によって初期化されたグローバルストアを取得しようとします。このストアは、実行中の実験で設定された `init_store_function_name` によって指定された名前を持ちます。このストアは各ワーカーにローカルです。

# セットアップ

ストアを作成するには、インクルードファイルに辞書型 Dict{Symbol, Any} を返す関数を追加します。この関数は次のようなシグネチャを持ちます。

```julia
function create_global_store(config)
    # config は実験に与えられたグローバル設定です
    data = Dict{Symbol, Any}(
        :dataset => rand(1000),
        :flag => false,
        # etc...
    )
    return data
end
```

メインの実験実行関数内で、`Experimenter` によってエクスポートされた `get_global_store` を使用してこのストアを取得できます。

```julia
function myrunner(config, trial_id)
    store = get_global_store()
    dataset = store[:dataset] # ストアからキーを取得
    # データを処理
    return results
end
```
