```
parse_constraint_head(_error::Function, ::Val{head}, args...)
```

このメソッドを実装して、`head`を持つ式の解析を intercept します。

!!! warning
    制約マクロを解析時に拡張することは高度な操作であり、既存の JuMP 構文に干渉する可能性があります。これらのメソッドを実装するコードを公開する前に、[開発者チャットルーム](https://gitter.im/JuliaOpt/jump-dev)で相談してください。


## 引数

  * `_error`: `String`を受け取り、その文字列をエラーとしてスローする関数で、スローされたマクロのいくつかの説明情報を含みます。
  * `head`: intercept する `Expr` の `.head` フィールド
  * `args...`: `Expr` の `.args` フィールド。

## 戻り値

この関数は次のものを返さなければなりません：

  * `is_vectorized::Bool`: 式が `x .<= 1` のようなブロードキャストされた式を表すかどうか
  * `parse_code::Expr`: `build_constraint` の前に呼び出す必要があるセットアップまたは書き換えコードを含む式
  * `build_code::Expr`: `is_vectorized` に応じて `build_constraint(` または `build_constraint.(` を呼び出す式。

## 既存の実装

JuMP は現在次のものを実装しています：

  * `::Val{:call}`、これは [`parse_constraint_call`](@ref) への呼び出しを転送します
  * `::Val{:comparison}`、これは `l <= body <= u` の特別なケースを処理します。

参照： [`parse_constraint_call`](@ref)、[`build_constraint`](@ref)
