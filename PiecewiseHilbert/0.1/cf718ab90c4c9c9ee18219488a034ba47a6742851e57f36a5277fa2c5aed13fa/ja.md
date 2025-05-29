```
HilbertTransform(f::PiecewiseFunction [, radius::Real])
```

区分関数 `f` のための `HilbertTransform` オブジェクトのコンストラクタ。モーメント展開は複素平面で |z| = radius を超えて使用されます。指定されていない場合、半径は自動的に設定されます。フィールド `error` は |z| = radius での絶対誤差の推定値を提供します。

## フィールド

  * `f::PiecewiseFunction`
  * `radius::Real`
  * `moments::Vector{Real}`
  * `error::Real`

## 例

ボックスのヒルベルト変換:

```julia-repl
julia> H = HilbertTransform(PiecewiseFunction(Piece((-1, 1), POLY, [1])))
< ヒルベルト変換の区分関数でサポート [-1.0, 1.0] >

julia> H.([1im, 10im, 100im])
3-element Vector{ComplexF64}:
 0.0 - 1.5707963267948966im
 0.0 - 0.19933730476190478im
 0.0 - 0.019999333333333334im
```
