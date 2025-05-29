```
headervalue(ghs::GameHeaders, name::String)
headervalue(g::SimpleGame, name::String)
headervalue(g::Game, name::String)
```

指定された名前のヘッダーの値を検索します。

提供された名前のヘッダーが存在しない場合は、値を `String` として返すか、`nothing` を返します。
