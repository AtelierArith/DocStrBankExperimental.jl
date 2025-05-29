```
InitGTPSA{D,DD}
```

[GTPSA.jl](https://github.com/bmad-sim/GTPSA.jl)バックエンドを使用してTPSAを定義するために使用される構造体。

[`TPSAInterface.jl`](https://github.com/bmad-sim/TPSAInterface.jl)によって定義されています。

# コンストラクタ

```
InitGTPSA{D,DD}(; dynamic_descriptor=nothing)
```

## フィールド

  * 静的`Descriptor`解決のために:

      * `D`は`Descriptor`
      * `DD`は`Nothing`で、`dynamic_descriptor`は`nothing`
  * 動的`Descriptor`解決のために:

      * `D == GTPSA.Dynamic`
      * `DD == Descriptor`で、`dynamic_descriptor`はその`Descriptor`と呼ばれます
