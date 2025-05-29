```
    PDPageObject
```

The content streams associated with PDF pages contain the objects that can be rendered. These objects are represented by `PDPageObject`. These objects can contain a postfix notation based operator prefixed by its operands like:

```
(Draw this text) Tj
```

As can be seen above, the string object is a [`CosString`](@ref) which is a parameter to the operand `Tj` or draw text. These class of objects are represented by [`PDPageElement`](@ref).

However, there are certain objects which only provide grouping information or begin and end markers for grouping information. For example, a text object:

```
BT
    /F1 11 Tf  %selectfont
    (Draw this text) Tj
ET
```

These kind of objects are represented by [`PDPageObjectGroup`](@ref). In this case, the [`PDPageObjectGroup`](@ref) contains four [`PDPageElement`](@ref). Namely, represented as operators `BT`, `Tf`, `Tj`, `ET`.

`PDPageElement` and [`PDPageObjectGroup`](@ref) can be extended by composition. Hence, there are more specialized objects that can be seen as well.
