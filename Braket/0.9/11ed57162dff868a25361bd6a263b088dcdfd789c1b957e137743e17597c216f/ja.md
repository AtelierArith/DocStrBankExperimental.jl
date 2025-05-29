```
ir(c::Circuit; serialization_properties::SerializationProperties=OpenQASMSerializationProperties())
```

[`Circuit`](@ref)を、ローカルシミュレーター、オンデマンドシミュレーター、またはQPUによって消費されるIRに変換します。デフォルトで変換するIR形式は、グローバル変数[`IRType`](@ref)によって制御されており、変更可能です。現在、`Circuit`に対しては`:JAQCD`と`:OpenQASM`がサポートされています。`OpenQASM` IRに書き込む場合、オプションの[`OpenQASMSerializationProperties`](@ref)を指定できます。
