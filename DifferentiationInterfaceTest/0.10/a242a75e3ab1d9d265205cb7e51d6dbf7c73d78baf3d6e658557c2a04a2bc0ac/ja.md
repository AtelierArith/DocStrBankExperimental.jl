```
Scenario{op,pl_op,pl_fun}
```

関数とその入力 + 出力から構成されるテストシナリオを、特定の演算子に対して保存します。

この汎用型は直接使用するべきではありません：テストしたい演算子に対応する特定のコンストラクタ、または事前定義されたシナリオのリストを使用してください。

# 型パラメータ

  * `op`: `:pushforward`、`:pullback`、`:derivative`、`:gradient`、`:jacobian`、`:second_derivative`、`:hvp`、`:hessian` のいずれか
  * `pl_op`: `:in`（`op!(f, result, backend, x)`の場合）または `:out`（`result = op(f, backend, x)`の場合）
  * `pl_fun`: `:in`（`f!(y, x)`の場合）または `:out`（`y = f(x)`の場合）

# コンストラクタ

```
Scenario{op,pl_op}(
    f, x, [t], contexts...;
    prep_args, res1, res2, name
)

Scenario{op,pl_op}(
    f!, y, x, [t,] contexts...;
    prep_args, res1, res2, name
)
```

デフォルト値:

  * `prep_args =` 各実行引数に適用された `zero` の結果
  * `res1 = res2 = nothing`
  * `name = nothing`

# フィールド

  * `f::Any`: 適用する関数 `f`（`pl_fun==:out`の場合）または `f!`（`pl_fun==:in`の場合）
  * `y::Any`: プライマル出力
  * `x::Any`: プライマル入力
  * `t::Union{Nothing, NTuple{N, T} where {N, T}}`: 接線（該当する場合）
  * `contexts::Tuple`: コンテキスト（該当する場合）
  * `res1::Any`: 演算子の一次結果（該当する場合）
  * `res2::Any`: 演算子の二次結果（該当する場合）
  * `prep_args::NamedTuple`: 準備に渡される引数の名前付きタプル、関数なし - 必要なキーは演算子に応じて `(; y, x, t, contexts)` のサブセットです
  * `name::Union{Nothing, String}`: テストセットやデータフレームに表示するためのシナリオの名前
