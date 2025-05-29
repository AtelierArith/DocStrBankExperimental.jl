```
GeometricBeam(w=0.0, k=0.0, z=0.0)
```

キーワードを使って幾何学的な光線ビームを定義します。軸までの距離は `w`、軸に対する角度は `k` です。`zpos` は光学軸に沿った初期位置です。

関連情報は [`GaussianBeam`](@ref) を参照してください。

## 例

```jldoctest
julia> GeometricBeam(w=1.0)
GeometricBeam{Float64}(1.0, 0.0, 0.0)
```
