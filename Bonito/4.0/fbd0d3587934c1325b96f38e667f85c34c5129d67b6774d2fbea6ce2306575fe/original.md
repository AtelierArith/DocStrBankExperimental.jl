```
Styles(css::CSS...)
```

Creates a Styles object, which represents a Set of CSS objects. You can insert the Styles object into a DOM node, and it will be rendered as a `<style>` node. If you assign it directly to `DOM.div(style=Style(...))`, the styling will be applied to the specific div. Note, that per `Session`, each unique css object in all `Styles` across the session will only be rendered once. This makes it easy to create Styling inside of components, while not worrying about creating lots of Style nodes on the page. There are a two more convenience constructors to make `Styles` a bit easier to use:

```julia
Styles(pairs::Pair...) = Styles(CSS(pairs...))
Styles(priority::Styles, defaults...) = merge(Styles(defaults...), priority)
```

For styling components, it's recommended, to always allow user to merge in customizations of a Style, like this:

```julia
function MyComponent(; style=Styles())
    return DOM.div(style=Styles(style, "color" => "red"))
end
```

All Bonito components are stylable this way.

!!! info
    Why not `Hyperscript.Style`? While the scoped styling via `Hyperscript.Style` is great, it makes it harder to create stylable components, since it doesn't allow the deduplication of CSS objects across the session. It's also significantly slower, since it's not as specialized on the deduplication and the camelcase keyword to css attribute conversion is pretty costly. That's also why `CSS` uses pairs of strings instead of keyword arguments.

