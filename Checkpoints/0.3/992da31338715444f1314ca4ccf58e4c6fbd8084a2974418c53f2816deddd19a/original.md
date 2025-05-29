```
with_checkpoint_tags(f::Function, context_tags::Pair...)
with_checkpoint_tags(f::Function, context_tags::NamedTuple)
```

Runs the function `f`, tagging any [`checkpoint`](@ref)s created by `f` with the `context_tags`. This is normally used via the do-block form: For example

```julia
with_checkpoint_tags(:foo=>1, :bar=>2) do
    q_out = qux()
    checkpoint("foobar"; :output=q_out)
end
```

This snippet will result in `"foobar"` checkpoint having the `foo=1` and `bar=2` tags, as will any checkpoints created by `qux`(). The context tags are [dynamically scoped](https://en.wikipedia.org/wiki/Scope_(computer_science)#Lexical_scope_vs._dynamic_scope_2) and so are retained through function calls.

Nested contexts (nested `with_checkpoint_tags` calls) are allowed. Duplicate tag names and values are allowed, including the tags provided directly in the [`checkpoint`](@ref) call. Duplicate tags are repeated, not overwritten.
