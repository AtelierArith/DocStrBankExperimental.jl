```
create_model(types::ModelTypes, name::String)
```

`Simulation`型のサブタイプである構造体を作成し、`types`の型情報に対応するメソッドをJuliaセッションに追加します。新しい構造体は`name`と名付けられ、すべてのメソッドはJuliaの多重ディスパッチの概念を使用してこの構造体に特有のものであるため、同じJuliaセッション内で異なるモデルを持つことが可能です（`name`が異なっている限り）。

具体的なシミュレーションを作成するために[`create_simulation`](@ref)で使用できる[`Model`](@ref)を返します。  
