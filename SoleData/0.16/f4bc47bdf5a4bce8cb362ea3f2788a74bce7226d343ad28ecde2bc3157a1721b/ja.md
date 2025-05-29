```
check(
    φ::SoleLogics.SyntaxTree,
    i::SoleLogics.LogicalInstance{<:AbstractModalLogiset{W,<:U}},
    w::Union{Nothing,AnyWorld,<:AbstractWorld} = nothing;
    kwargs...
)::Bool
```

与えられたインスタンス `i_instance` のログセット `X` に対して、世界 `w` で式 `φ` が成り立つかどうかを確認します。世界は、基礎的な式の場合は省略可能です（[`isgrounded`](@ref）を参照）。

この実装は、`φ` のサブフォーミュラを再帰的に評価し、エマーソン-クラークアルゴリズムを使用して結果をメモ化します。メモ化構造は、`X` 自体に保存されているもの（`X` がメモ化をサポートしている場合）か、`use_memo` 引数として渡された構造のいずれかです。`X` がワンステップメモ化をサポートしている場合、特定のダイヤモンド式に対して使用され、キーワード引数 `memo_max_height` に等しい高さまで使用されます。

# 引数

  * `φ::SoleLogics.SyntaxTree`: 確認する式。
  * `i::SoleLogics.LogicalInstance{<:AbstractModalLogiset{W,<:U}}`: 確認するログセットのインスタンス。
  * `w::Union{Nothing,AnyWorld,<:AbstractWorld} = nothing`: 確認する世界。`nothing` の場合、メソッドはインスタンスのすべての世界で確認します。

# キーワード引数

  * `use_memo::Union{Nothing,AbstractMemoset{<:AbstractWorld},AbstractVector{<:AbstractDict{<:FT,<:AbstractWorlds}}} = nothing`: 使用するメモ化構造。`nothing` の場合、メソッドは `X` に保存されているものを使用します（`X` がメモ化をサポートしている場合）。`AbstractMemoset` の場合、メソッドはメモ化構造の `i_instance` 番目の要素を使用します。`AbstractVector` の場合、メソッドはベクターの `i_instance` 番目の要素を使用します。
  * `perform_normalization::Bool = true`: 確認する前に式を正規化するかどうか。
  * `memo_max_height::Union{Nothing,Int} = nothing`: ワンステップメモ化を使用する最大の高さ。`nothing` の場合、メソッドはワンステップメモ化を使用しません。
  * `onestep_memoset_is_complete = false`: ワンステップメモ化構造が完全であるかどうか（すなわち、構造内のメタ条件のすべての可能な値を含んでいるか）。
