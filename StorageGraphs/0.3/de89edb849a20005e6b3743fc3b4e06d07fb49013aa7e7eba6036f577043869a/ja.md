```
function walkdep(g, dep::Pair; stopcond=(g,v)->false)
```

依存関係のチェーンに沿って移動しますが、既存のパスのみを対象とし、最後のノードと互換性のあるパスを返します。
