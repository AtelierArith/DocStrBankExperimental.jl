```
map_once(closure, inputs::Node....)::Node
```

Like Reactive.foreach, in the sense that it will be preserved even if no reference is kept. The difference is, that you can call map once multiple times with the same closure and it will close the old result Node and register a new one instead.

``` function test(s1::Node)     s3 = map*once(x-> (println("1 ", x); x), s1)     s3 = map*once(x-> (println("2 ", x); x), s1)

end test(Node(1), Node(2))

>

