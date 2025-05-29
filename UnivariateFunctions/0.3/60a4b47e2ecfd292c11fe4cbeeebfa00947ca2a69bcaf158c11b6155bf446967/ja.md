```
change_base_of_PE_Function(f::PE_Function, new_base::Real)
```

これは `PE_Function` の基数を変更します。したがって、基数が2の場合、追加の定数項を使用して3に変換できます。

### 入力

  * `f` - `PE_Function`。
  * `new_base` - 新しい基数。

### 戻り値

  * `PE_Function` または `Sum_Of_Functions`。
