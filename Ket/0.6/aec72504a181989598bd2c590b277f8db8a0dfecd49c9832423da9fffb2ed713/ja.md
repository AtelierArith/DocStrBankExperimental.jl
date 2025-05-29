```
n_body_basis(
n::Integer,
n_parties::Integer;
sb::AbstractVector{<:AbstractMatrix} = [pauli(1), pauli(2), pauli(3)],
eye::AbstractMatrix = I(size(sb[1], 1))
```

`n_parties`に作用する`n`個の非自明演算子の基底を返します。デフォルトではスパースパウリ行列を使用します。

例えば、`n_body_basis(2, 3)`は2つのパウリと1つの単位行列のすべての積を生成します。したがって、${X ⊗ X ⊗ 1, X ⊗ 1 ⊗ X, ..., X ⊗ Y ⊗ 1, ..., 1 ⊗ Z ⊗ Z}$のようになります。

パウリの代わりに、パラメータ`sb`で基底を提供することができ、単位行列は`eye`で変更できます。

この関数はジェネレーターを返し、これを使用してforループなどで全基底を一度に完全に割り当てることなく使用できます。ベクターが必要な場合は、`collect`を呼び出してください。
