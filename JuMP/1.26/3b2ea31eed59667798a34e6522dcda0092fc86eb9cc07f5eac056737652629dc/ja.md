```
parse_constraint_call(
    error_fn::Function,
    is_vectorized::Bool,
    ::Val{op},
    args...,
)
```

このメソッドを実装して、演算子 `op` を持つ `:call` 式の解析を intercept します。

!!! warning
    制約マクロを解析時に拡張することは高度な操作であり、既存の JuMP 構文に干渉する可能性があります。これらのメソッドを実装するコードを公開する前に、[開発者チャットルーム](https://gitter.im/JuliaOpt/jump-dev) で相談してください。


## 引数

  * `error_fn`: `String` を受け取り、その文字列をエラーとしてスローする関数で、スローされたマクロの説明情報も含まれます。
  * `is_vectorized`: `op` をブロードキャストするかどうかを示すブール値
  * `op`: intercept する `Expr` の `.args` フィールドの最初の要素
  * `args...`: `Expr` の `.args` フィールド。

## 戻り値

この関数は次のものを返さなければなりません：

  * `parse_code::Expr`: `build_constraint` の前に呼び出す必要があるセットアップまたは書き換えコードを含む式
  * `build_code::Expr`: `is_vectorized` に応じて `build_constraint(` または `build_constraint.(` を呼び出す式

関連情報: [`parse_constraint_head`](@ref), [`build_constraint`](@ref)
