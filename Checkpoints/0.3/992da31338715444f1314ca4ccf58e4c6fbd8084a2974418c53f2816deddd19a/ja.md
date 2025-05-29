```
with_checkpoint_tags(f::Function, context_tags::Pair...)
with_checkpoint_tags(f::Function, context_tags::NamedTuple)
```

関数 `f` を実行し、`f` によって作成された [`checkpoint`](@ref) に `context_tags` でタグ付けします。これは通常、doブロック形式で使用されます。例えば

```julia
with_checkpoint_tags(:foo=>1, :bar=>2) do
    q_out = qux()
    checkpoint("foobar"; :output=q_out)
end
```

このスニペットは、`"foobar"` チェックポイントが `foo=1` と `bar=2` のタグを持つことになり、`qux`() によって作成されたチェックポイントも同様です。コンテキストタグは [動的スコープ](https://en.wikipedia.org/wiki/Scope_(computer_science)#Lexical_scope_vs._dynamic_scope_2) であり、関数呼び出しを通じて保持されます。

ネストされたコンテキスト（ネストされた `with_checkpoint_tags` 呼び出し）は許可されています。重複するタグ名と値は許可されており、[`checkpoint`](@ref) 呼び出しで直接提供されたタグも含まれます。重複するタグは繰り返され、上書きされることはありません。
