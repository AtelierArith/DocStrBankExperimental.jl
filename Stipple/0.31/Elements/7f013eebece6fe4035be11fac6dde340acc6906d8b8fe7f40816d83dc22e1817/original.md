```
@showif(expr, [type])
```

v-show will always be rendered and remain in the DOM; v-show only toggles the display CSS property of the element. [https://vuejs.org/v2/guide/conditional.html#v-show](https://vuejs.org/v2/guide/conditional.html#v-show)

Difference between @showif and @iif when to use either

v-if has higher toggle costs while v-show has higher initial render costs

### Example

```julia
julia> h1("Hello!", @showif(:ok))
"<h1 v-show="ok">Hello!</h1>"
```
