```
function update(widget; force_redraw = false)
```

ウィジェットを `redraw` 関数を呼び出すことで更新します。この関数は、ウィジェットが更新される必要があった場合は `true` を、そうでない場合は `false` を返します。

`force_redraw` が `true` の場合、必要でなくてもウィジェットは更新されます。
