```
const Variable = Core.SSAValue
var(id::Int) = Variable(id)
```

`Core.SSAValue` のエイリアス – 低下したコードにおけるプリミティブレジスタを表します。詳細については、Juliaのドキュメントの[低下した形式](https://docs.julialang.org/en/v1/devdocs/ast/#Lowered-form)のセクションを参照してください。
