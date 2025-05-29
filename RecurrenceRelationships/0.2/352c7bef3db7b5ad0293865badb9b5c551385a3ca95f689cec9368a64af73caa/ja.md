clenshaw!(f::AbstractVecOrMat, c::AbstractVecOrMat, A, B, C, x::Number)

は、DLMFで定義された再帰係数を含む`AbstractVector`である`A`、`B`、`C`を用いて、係数`c`を点`x`で評価し、結果で`f`を上書きします。

`c`が行列の場合、これは各行（`size(f,2) == 1`の場合）または列（`size(f,1) == 1`の場合）を別々の係数ベクトルとして扱います。
