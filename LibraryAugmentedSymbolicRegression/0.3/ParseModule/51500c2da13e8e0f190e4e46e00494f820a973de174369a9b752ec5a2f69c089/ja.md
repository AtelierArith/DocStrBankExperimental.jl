```
render_expr(ex::AbstractExpression{T}, options::AbstractOptions) -> String
```

与えられた AbstractExpression と options オブジェクトに基づいて、式の文字列表現を返します。具体的には、定数を "C" に置き換え、変数を "x"、"y"、"z" など、または事前に指定された変数名に置き換えます。
