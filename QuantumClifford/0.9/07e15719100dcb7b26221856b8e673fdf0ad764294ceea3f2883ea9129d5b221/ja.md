内積の対数は、2つの安定器状態の間のものです。

結果が `nothing` の場合、ドット内積はゼロです。それ以外の場合、内積は `2^(-logdot/2)` です。

実際の内積は `LinearAlgebra.dot` を使用して計算できます。

[garcia2012efficient](@cite) に基づいています。
