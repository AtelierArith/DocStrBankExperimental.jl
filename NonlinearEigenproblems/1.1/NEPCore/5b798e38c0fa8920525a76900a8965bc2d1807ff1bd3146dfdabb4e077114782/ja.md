```
abstract type Logger ; end
```

この型は、アルゴリズム全体で情報をログする方法を表します。エラーヒストリーやその他のプロパティはロガーに保存できます。最も一般的な `Logger` は `PrintLogger` と `ErrorLogger` です。

メソッド開発者として、[`push_info!`](@ref) と [`push_iteration_info!`](@ref) を使用したいと思います。

関連情報: [`PrintLogger`](@ref) と [`ErrorLogger`](@ref)。
