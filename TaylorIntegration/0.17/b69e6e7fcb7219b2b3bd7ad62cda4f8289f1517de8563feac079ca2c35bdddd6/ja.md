`@taylorize expr`

このマクロは、`expr`で与えられた関数を`eval`し、その関数に特化した[`jetcoeffs!`](@ref)の新しいメソッドを定義します。マクロを使用した後に[`lyap_taylorinteg`](@ref)の[`taylorinteg`](@ref)を介して統合すると、より良いパフォーマンスが得られます。

詳細と制限については、[documentation](@ref taylorize)を参照してください。

!!! warning
    このマクロは実験段階にあります。統合結果を注意深く確認してください。

