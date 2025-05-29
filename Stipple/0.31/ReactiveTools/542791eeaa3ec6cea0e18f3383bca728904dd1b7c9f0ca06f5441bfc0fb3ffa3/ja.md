```
@watch(expr)
@watch(App, expr)
```

vue要素の`watch`セクションのためのjs関数を定義します。

`expr`は以下のいずれかであることができます。

  * javascriptコードを含む`String`
  * 関数名と関数コードの`Pair`
  * javascriptコードの`String`を返す`Function`
  * 関数名と関数コードの`Dict`
  * 上記の`Vector`

### 例 1

```julia
@watch "greet: function(name) {console.log('Hello ' + name)}"
```

### 例 2

```julia
js_greet() = :greet => "function(name) {console.log('Hello ' + name)}"
js_bye() = :bye => "function() {console.log('Bye!')}"
@watch MyApp [js_greet, js_bye]
```

結果を確認するには、以下の方法で行うことができます。

```
julia> render(MyApp())[:watch].s |> println
{
    "greet":function(name) {console.log('Hello ' + name)},
    "bye":function() {console.log('Bye!')}
}
```
