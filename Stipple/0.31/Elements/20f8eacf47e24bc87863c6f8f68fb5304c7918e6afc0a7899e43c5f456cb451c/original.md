```
`@click(expr, modifiers = [])`
```

Defines a js routine that is called by a click of the quasar component. If a symbol argument is supplied, `@click` sets this value to true.

`@click("savefile = true")` or `@click("myjs_func();")` or `@click(:button)`

Modifers can be appended as String, Symbol or array of String/Symbol:

```
@click(:foo, :stop)
# "v-on:click.stop='foo = true'"

@click("foo = bar", [:stop, "prevent"])
# "v-on:click.stop.prevent='foo = bar'"
```
