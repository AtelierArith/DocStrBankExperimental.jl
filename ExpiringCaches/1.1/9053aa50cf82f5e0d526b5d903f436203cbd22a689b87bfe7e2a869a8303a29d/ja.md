```
@cacheable timeout function_definition::ReturnType
```

関数定義（`function_definition`、ショートフォームまたはフルフォームのいずれか）に対して、`ExpiringCaches.Cache`を作成し、結果を`timeout`のために保存します（明らかに正確な入力引数によってハッシュ化されます）。

関数定義には`ReturnType`宣言が*必須*であり、これは`Cache`内の値（`V`）タイプとして使用されます。
