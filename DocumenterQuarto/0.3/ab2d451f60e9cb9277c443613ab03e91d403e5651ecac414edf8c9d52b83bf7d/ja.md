```julia
autodoc(mod, symbols; delimiter)

```

指定されたモジュール内のシンボルに関するドキュメントを自動的に処理して返します。シンボルが提供されていない場合は、すべてのエクスポートされたシンボルが使用されます。`delimiter`キーワード引数は、各文書化された名前の間に印刷されます。

## 例

```julia
import LinearAlgebra
DocumenterQuarto.autodoc(LinearAlgebra)
```
