```
register_param!(types::ModelTypes, name::Symbol, default_value::T)
```

シミュレーションのパラメータを設定する方法は2つあります。モデル作成者によって定義された構造体のインスタンスを`param`引数を介して[`create_simulation`](@ref)に渡すか、[`create_model`](@ref)が呼び出される前に`register_param!`を使用して個々のパラメータを渡す必要があります。パラメータはまた、[`create_simulation`](@ref)の後、[`finish_init!`](@ref)が呼び出される前に設定することもできます。

`register_param!`のパイプ可能なバージョンも利用可能で、`register_*`呼び出しのシーケンスを介してモデルを構築することができます。このパイプラインは、`ModelTypes()`をソースとして開始し、[`create_model`](@ref)関数を宛先として終了します。
