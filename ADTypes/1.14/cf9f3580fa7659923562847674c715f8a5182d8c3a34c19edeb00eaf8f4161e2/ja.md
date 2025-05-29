```
AutoGTPSA{D}
```

自動微分のために[GTPSA.jl](https://github.com/bmad-sim/GTPSA.jl)バックエンドを選択するために使用される構造体。

[ADTypes.jl](https://github.com/SciML/ADTypes.jl)によって定義されています。

# コンストラクタ

```
AutoGTPSA(; descriptor=nothing)
```

# フィールド

  * `descriptor::D`: 次のいずれかであることができます。

      * 変数/パラメータの数、パラメータの順序、個々の変数/パラメータの切り捨て順序、および最大順序を指定するGTPSA `Descriptor`。詳細については、[GTPSA.jlのドキュメント](https://bmad-sim.github.io/GTPSA.jl/stable/man/b_descriptor/)を参照してください。
      * コンテキストに応じて自動的に`Descriptor`を使用するための`nothing`。
