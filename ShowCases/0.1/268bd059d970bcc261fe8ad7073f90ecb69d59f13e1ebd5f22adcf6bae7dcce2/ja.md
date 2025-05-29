```
ShowKw(o, name, separator=Print("="); kw...)
ShowKw(o, name::Symbol, separator=Print("="); kw...)
```

オブジェクトをキーワード引数のように `name` という名前で表示します。例えば `ShowKw(x, :x)` は `x=x` と表示します。

## コンストラクタ

  * `o`: ラップされるオブジェクト。
  * `name`: オブジェクトの名前。`Symbol` の場合はキーワード引数のように表示されます。
  * `separator`: 名前と表示されるオブジェクトの間の区切り文字。
  * `kw`: [`ShowList`](@ref) に渡されるキーワード引数。
