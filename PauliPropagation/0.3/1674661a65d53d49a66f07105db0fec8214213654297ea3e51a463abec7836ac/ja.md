```
FrozenGate(gate::ParametrizedGate, parameter::Number)
```

`StaticGate`は、固定されたパラメータを持つ`ParametrizedGate`をラップします。これは、回路構築時に`ParametrizedGate`のパラメータを固定するために使用されます。これは便利ですが、このパラメータが外部ライブラリによって微分されることを除外する可能性があります。
