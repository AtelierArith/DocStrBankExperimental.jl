```
remake(prob::AbstractSciMLProblem; u0 = missing, p = missing, interpret_symbolicmap = true, use_defaults = false)
```

与えられた問題 `prob` を再構築します。`u0` または `p` が指定されている場合、それらは問題の未知数/パラメータの代わりに使用されます。どちらも、問題に関連するシステムがある場合は、シンボリックマップである可能性があります。`interpret_symbolicmap == false` の場合、`p` は決してシンボリックマップとして解釈されず、そのままパラメータとして使用されます。`use_defaults` は、シンボリックマップに渡された `u0` または `p` の欠損値を計算するためにシステムからのデフォルト値が使用されるかどうかを制御します。これは、`u0` または `p` が明示的にシンボリックマップとして提供され、問題に関連するシステムがある場合にのみ有効です。
