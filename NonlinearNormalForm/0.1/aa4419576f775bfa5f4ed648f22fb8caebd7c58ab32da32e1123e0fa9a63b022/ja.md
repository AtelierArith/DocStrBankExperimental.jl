VectorField(h::TPS; Q::Union{Quaternion,Nothing}=nothing, spin::Union{Bool,Nothing}=nothing)

渡されたハミルトニアン `h` から `VectorField` を構築します。具体的には、`h` に対して、次のようなベクトル場 `F` を構築します。

`F.x = [-∂h/∂p₁, ∂h/∂q₁, ...]`
