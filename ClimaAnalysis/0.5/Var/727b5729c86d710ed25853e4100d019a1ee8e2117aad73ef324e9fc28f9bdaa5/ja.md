```
replace(var::OutputVar, old_new::Pair...)
```

`OutputVar`を返します。ここで、各ペア`old  => new`について、`Var.data`内の`old`のすべての出現が`new`に置き換えられます。

この関数は、データに`NaN`や`missing`値がある場合に便利です。たとえば、海洋マスクを使用したいが、海洋に`NaN`がある場合です。すべての`NaN`と`missing`値を0.0に置き換え、その後に海洋マスクを適用できます。
