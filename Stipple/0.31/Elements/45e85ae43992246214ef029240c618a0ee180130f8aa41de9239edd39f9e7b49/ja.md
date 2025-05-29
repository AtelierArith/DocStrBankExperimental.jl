```
@jsexpr(expr)
```

Julia式からJS式を生成します。これは、文字列として渡す必要があるVue.js式を作成するのに便利です。これらは`json()`によって変更されることなく、まさに`JSONText`のようにそのままテキストとしてレンダリングされます。

### 例

```julia julia> @jsexpr(:a + :b) JSExpr("(a + b)")

```
