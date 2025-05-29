```
@process f(arg...) [cycles]
```

関数 `f(arg...)` からプロセスを作成します。

関数とその引数を [`Prc`](@ref) でラップし、[`process!`](@ref) で開始します。

# 引数

  * `f`: 関数、
  * `arg...`: 引数、最初の引数は AbstractClock でなければなりません、
  * `cycles::Int`: `f` が実行されるサイクル数。

# 戻り値

  * `Int` 型のプロセス ID。
