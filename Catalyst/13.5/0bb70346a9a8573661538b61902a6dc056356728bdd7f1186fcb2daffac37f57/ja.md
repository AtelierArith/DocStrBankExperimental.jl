```
numreactionparams(network)
```

与えられた [`ReactionSystem`](@ref) および `ReactionSystem` であるサブシステム内のパラメータの総数を返します。

注意

  * サブシステムがない場合、これは高速です。
  * これは [`reactionparams`](@ref) を呼び出すため、サブシステムがある場合は遅くなり、メモリを割り当てる可能性があります。
