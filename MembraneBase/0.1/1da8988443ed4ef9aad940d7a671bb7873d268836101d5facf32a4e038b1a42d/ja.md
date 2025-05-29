```
concentration(isotherm::IsothermData; component=nothing, gas_units=:cc, pol_units=:cc)
```

特定の単位で等温線内の成分の濃度を取得します。

# 引数

  * `gas_units`: ペネトレントの単位。

      * 指定可能: `:g`, `:cc`

!!! note
    `gas_units`は実際には`penetrant_units`であるべきです。なぜなら、液相の等温線も存在するからです。今のところ、これらは同義語と考えてください。


  * `polymer_units`: ポリマーの単位。

      * 指定可能: `:g`, `:cc`

例えば `concentration(some_isotherm; gas_units=:g, pol_units=:cc)` は、$\frac{g}{CC_{polymer}}$の単位で成分濃度を取得します。

!!! warning
    このメソッドは最適化されていません。実際、`concentration`が呼び出されるたびに、すべての等温線成分が指定された単位に変換されます。したがって、パフォーマンスが重要であり、すべての濃度が必要な場合は、一度にすべてを取得し、必要に応じて反復処理してください。

