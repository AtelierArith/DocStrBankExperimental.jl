```
Cols(cols...; operator=union)
Cols(f::Function; operator=union)
```

`cols`で指定された条件に一致する列を選択します。`cols == ()`の場合、列は選択されません。

唯一の位置引数が`Function` `f`の場合、`f`の述語に文字列として渡された列名が`true`を返す列を選択します。

複数の`cols`セレクタが渡されると、それらによって選択された列の集合が位置引数として`operator`に渡されます。`operator`は、Base Juliaで定義された`union`、`intersect`、`setdiff`、`symdiff`のような集合演算関数である必要があります。デフォルトでは`operator=union`であり、この場合、少なくとも1つのセレクタに一致するすべての列が返されます。
