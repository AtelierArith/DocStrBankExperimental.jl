```
LorentzTransform(f::PiecewiseFunction, m::Integer [, ground::Real=1e-10])
```

`f`のための`LorentzTransform`オブジェクトのコンストラクタ。`m`は変換の次数です。変換の結果が`ground`より小さい場合、モーメント展開が使用されます。

## フィールド

  * `f::PiecewiseFunction`
  * `m::Integer`
  * `ground::Real`
  * `moments::Vector{Real}`

## 例

箱の$L^2$変換:

```julia-repl
julia> L = LorentzTransform(PiecewiseFunction(Piece((-1, 1), POLY, [1])), 2)
< L^2 transform of piecewise function with support [-1.0, 1.0] >

julia> L(0, -im)
0.13023806336711655
```
