```
inspect(T::DataType; documentation::Bool=false, constructors::Bool=true, methods::Bool=true, supertypes::Bool=true)
```

`DataType`を検査して、ドキュメント文字列、コンストラクタ、メソッドなどの情報を表示します。フラグを使用して、提示される情報の詳細レベルを選択できます：

  * documentation: `termshow`でドキュメント文字列を表示
  * constructors: `T`のコンストラクタを表示
  * methods: シグネチャに`T`を使用するメソッドを表示
  * supertypes: シグネチャに`T`のスーパタイプを使用するメソッドを表示
