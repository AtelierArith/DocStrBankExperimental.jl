```
const Variable = Core.SSAValue
var(id::Int) = Variable(id)
```

`Core.SSAValue` のエイリアス – 低下したコードにおけるプリミティブレジスタを表します。詳細については、Juliaのドキュメントの [lowered forms](https://docs.julialang.org/en/v1/devdocs/ast/#Lowered-form) のセクションを参照してください。
