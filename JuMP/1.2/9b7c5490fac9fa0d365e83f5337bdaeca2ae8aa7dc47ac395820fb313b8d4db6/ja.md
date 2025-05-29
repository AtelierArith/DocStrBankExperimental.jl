```
parse_constraint(_error::Function, expr::Expr)
```

すべての制約関連の解析のエントリーポイントです。

## 引数

  * `_error` 関数は、より良いエラーメッセージを提供するためにどこにでも渡されます
  * `expr` は `@constraint` マクロから来ます。2つの可能性があります：

      * `@constraint(model, expr)`
      * `@constraint(model, name[args], expr)`

    どちらの場合も、`expr` は制約の主要なコンポーネントです。

## サポートされている構文

JuMP は現在、以下の `expr` オブジェクトをサポートしています：

  * `lhs <= rhs`
  * `lhs == rhs`
  * `lhs >= rhs`
  * `l <= body <= u`
  * `u >= body >= l`
  * `lhs ⟂ rhs`
  * `lhs in rhs`
  * `lhs ∈ rhs`
  * `z => {constraint}`
  * `!z => {constraint}`

およびすべてのブロードキャストされたバリアント。

## 拡張

`parse_constraint` の背後にあるインフラストラクチャは拡張可能です。詳細については [`parse_constraint_head`](@ref) と [`parse_constraint_call`](@ref) を参照してください。
