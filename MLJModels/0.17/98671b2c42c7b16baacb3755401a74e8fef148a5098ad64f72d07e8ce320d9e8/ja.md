```
load_path(model_name::String, pkg=nothing)
```

`model_name`という名前のモデルタイプのロードパスを返します。必要に応じて名前の競合を解決するためにアルゴリズムを提供するパッケージ名`pkg`を指定します。

```
load_path(proxy::NamedTuple)
```

`proxy.name`という名前のモデルのロードパスを返します。また、アルゴリズムを提供するパッケージの名前は`proxy.package_name`です。例えば、`proxy`は`models()`によって返されるベクターの任意の要素である可能性があります。

```
load_path(model)
```

`model`インスタンスまたはタイプのロードパスを返します。通常、必要なモデルコードが別途ロードされている必要があります。コードがロードされていない場合は、上記のように文字列を供給してください。
