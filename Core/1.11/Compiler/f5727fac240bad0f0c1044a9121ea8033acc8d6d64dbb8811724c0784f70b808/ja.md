```
AbstractInterpreter
```

抽象基底クラスで、複数のディスパッチを使用してJuliaコードの実行方法を決定します。この抽象クラスの具体的なインスタンスである`NativeInterpreter`を使用することで、ネイティブなJulia-LLVMパイプラインが有効になります。他のインスタンスも`AbstractInterpreter` APIに従う限り、入れ替えることができます。

`interp::NewInterpreter`が`AbstractInterpreter`である場合、`AbstractInterpreter` APIの要件を満たすために、少なくとも以下のメソッドを提供することが期待されます：

  * `InferenceParams(interp::NewInterpreter)` - `InferenceParams`インスタンスを返す
  * `OptimizationParams(interp::NewInterpreter)` - `OptimizationParams`インスタンスを返す
  * `get_inference_world(interp::NewInterpreter)` - このインタープリタのワールドエイジを返す
  * `get_inference_cache(interp::NewInterpreter)` - ローカル推論キャッシュを返す
  * `cache_owner(interp::NewInterpreter)` - 新しいキャッシュエントリの所有者を返す
