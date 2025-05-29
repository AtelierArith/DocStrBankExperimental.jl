```
register_global!(types::ModelTypes, name::Symbol, default_value::T)
```

シミュレーションのためのグローバルを設定する方法は2つあります。モデル作成者によって定義された構造体のインスタンスを`globals`引数を介して[`create_simulation`](@ref)に渡すか、個々のパラメータを`register_global!`を使用して[`create_model`](@ref)が呼び出される前に渡す必要があります。

`register_global!`のパイプ可能なバージョンも利用可能で、`register_*`呼び出しのシーケンスを介してモデルを構築することができます。このパイプラインは`ModelTypes()`をソースとして開始し、[`create_model`](@ref)関数を宛先として終了します。
