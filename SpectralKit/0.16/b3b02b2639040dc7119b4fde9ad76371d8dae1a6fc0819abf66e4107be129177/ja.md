`basis_at(basis, x)`

`basis`で評価された`x`の基底関数の既知の要素型と長さ（`Base.HasEltype()`, `Base.HasLength()`）を持つ反復可能なオブジェクトを返します。

単変数基底は実数で動作し、多変数基底の場合は、パフォーマンスのために`Tuple`または`StaticArrays.SVector`が推奨されますが、すべての`<:AbstractVector`型が機能するはずです。

メソッドは型安定です。

!!! note
    定義域の外で評価すると結果は未定義です。

