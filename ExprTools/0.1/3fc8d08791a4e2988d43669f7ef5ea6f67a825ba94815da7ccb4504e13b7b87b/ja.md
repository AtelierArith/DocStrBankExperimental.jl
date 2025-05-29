```
splitdef(ex::Expr; throw::Bool=true) -> Union{Dict{Symbol,Any}, Nothing}
```

関数定義式をそのさまざまなコンポーネントに分割します。これには以下が含まれます：

  * `:head`: 関数定義の式のヘッド（`:function`、`:(=)`、`:(->)`）
  * `:name`: 関数の名前（匿名関数には存在しません）
  * `:params`: コンストラクタで定義されたパラメトリック型
  * `:args`: 関数の位置引数
  * `:kwargs`: 関数のキーワード引数
  * `:rtype`: 関数の戻り値の型
  * `:whereparams`: Whereパラメータ
  * `:body`: 関数の本体（空の関数には存在しません）

リストされたすべてのコンポーネントは、`：head`を除いて、返される辞書に存在しない場合があります。`：head`は常に存在します。

提供された式が関数でない場合、`throw=true`のときに例外が発生します。例外を発生させずに`nothing`を返すには、`throw=false`を使用してください。

参照： [`combinedef`](@ref)
