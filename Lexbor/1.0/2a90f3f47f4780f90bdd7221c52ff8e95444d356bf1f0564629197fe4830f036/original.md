```
is_comment(node::Node) -> Bool
```

Is `node` a comment `Node`? E.g. `<!-- ... -->` syntax.

Use [`comment`](@ref Lexbor.comment) to access the `String` contents of the comment.
