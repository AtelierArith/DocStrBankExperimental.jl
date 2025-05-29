```
transform(Rs::DirectBasis, P::AbstractMatrix{<:Real})
```

変換行列 `P` $= \mathbf{P}$ の下で直接基底 `Rs` $= (\mathbf{a}\ \mathbf{b}\ \mathbf{c})$ を変換し、`Rs′` $= (\mathbf{a}'\ \mathbf{b}'\ \mathbf{c}') = (\mathbf{a}\ \mathbf{b}\ \mathbf{c}) \mathbf{P}$ を返します。
