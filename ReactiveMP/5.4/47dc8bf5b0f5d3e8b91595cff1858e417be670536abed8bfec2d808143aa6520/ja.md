```
constrain_form(wrapped::WrappedFormConstraint, something)
```

この関数は `wrapped` オブジェクトをアンラップし、提供されたコンテキストで `constrain_form` 関数を呼び出します。コンテキストが提供されていない場合は、単にラップされた制約で `constrain_form` を呼び出します。それ以外の場合は、コンテキストを第二引数として `constrain_form` 関数に渡します。
