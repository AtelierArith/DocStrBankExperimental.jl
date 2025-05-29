```
compare_fields(s1, s2; silent::Bool = false)
```

同じ型の2つの構造体の各データフィールドのデータを比較します。

**引数:**

  * `s1`:     構造体1
  * `s2`:     構造体2
  * `silent`: （オプション）trueの場合、要約を出力しない

**戻り値:**

  * `N_dif`: `silent = false`の場合、異なるフィールドの数
