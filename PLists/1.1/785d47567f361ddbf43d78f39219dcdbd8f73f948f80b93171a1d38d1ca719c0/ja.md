```
locatefirst(name, attribute, value, node) -> Node
```

`name`が`attribute`に`value`を持つ最初のノードを見つけます。例えば、ノード`<egg foobar="spam"/>`を見つけるには、次のように書くことができます:     locatefirst("egg", "foobar", "spam", parent_node)
