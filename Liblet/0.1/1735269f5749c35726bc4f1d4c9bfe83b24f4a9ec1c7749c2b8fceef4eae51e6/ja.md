```
possiblesteps(d::Derivation; prod::Union{Int, Nothing} = nothing, pos::Union{Int, Nothing} = nothing)
```

文法と現在の*文形式*に基づいて実行可能なすべてのステップを返します。

文法の生成物の左辺に対応する*文形式*のすべての位置を特定し、位置と生成物番号を返します。生成物が指定されている場合、それに関連するペアのみを返します。同様に、位置が指定されている場合、それに関連するペアのみを返します。
