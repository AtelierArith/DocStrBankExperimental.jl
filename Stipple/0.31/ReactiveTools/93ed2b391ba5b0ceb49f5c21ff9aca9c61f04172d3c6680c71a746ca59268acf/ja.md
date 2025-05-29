```
@computed(expr)
@computed(App, expr)
```

vue要素の`computed`セクションのためのjs関数を定義します。

`expr`は以下のいずれかです。

  * javascriptコードを含む`String`
  * 関数名と関数コードの`Pair`
  * javascriptコードのStringを返す`Function`
  * 関数名と関数コードの`Dict`
  * 上記の`Vector`

### 例 1

```julia
@computed "greet: function(name) {console.log('Hello ' + name)}"
```

### 例 2

```julia
js_greet() = :greet => "function(name) {console.log('Hello ' + name)}"
js_bye() = :bye => "function() {console.log('Bye!')}"
@computed MyApp [js_greet, js_bye]
```

結果の確認は以下の方法で行えます。

```
julia> render(MyApp())[:computed].s |> println
{
    "greet":function(name) {console.log('Hello ' + name)},
    "bye":function() {console.log('Bye!')}
}
```
