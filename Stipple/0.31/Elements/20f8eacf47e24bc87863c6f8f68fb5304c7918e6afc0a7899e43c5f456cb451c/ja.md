```
`@click(expr, modifiers = [])`
```

クアサーコンポーネントのクリックによって呼び出されるjsルーチンを定義します。シンボル引数が提供されると、`@click`はこの値をtrueに設定します。

`@click("savefile = true")` または `@click("myjs_func();")` または `@click(:button)`

修飾子は文字列、シンボル、または文字列/シンボルの配列として追加できます：

```
@click(:foo, :stop)
# "v-on:click.stop='foo = true'"

@click("foo = bar", [:stop, "prevent"])
# "v-on:click.stop.prevent='foo = bar'"
```
