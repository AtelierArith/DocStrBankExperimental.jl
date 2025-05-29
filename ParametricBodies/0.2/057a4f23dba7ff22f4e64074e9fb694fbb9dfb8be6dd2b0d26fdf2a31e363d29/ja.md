```
ParametricBody{T::Real}(curve,locate) <: AbstractBody

- `curve(u,t)` パラメトリックに定義された曲線
- `dotS(u,t)=derivative(t->curve(u,t),t)` 曲線の時間微分
- `locate(ξ,t)` パラメータ `u` を `ξ` に最も近いものを見つけるメソッド
- `map(x,t)=x` `x` から `ξ` へのマッピング
- `scale=|∇map|⁻¹` `ξ` から `x` への距離スケーリング
- `thk=0` 符号付き距離の厚さオフセット
- `boundary=true` 曲線が空間曲線ではなく、ボディ境界を表す場合

明示的に不安定なパラメトリック曲線によって幾何学を定義します。曲線は現在、単変数に制限されており、閉じている場合は反時計回りに巻く必要があります。オプションの `dotS`、`map`、`scale`、`thk` および `boundary` パラメータは、より一般的な幾何学的埋め込みを可能にします。

例:

```

curve(θ,t) = SA[cos(θ+t),sin(θ+t)] locate(x::SVector{2},t) = atan(x[2],x[1])-t body = ParametricBody(curve,locate)

@test body.curve(body.locate(SA[4.,3.],1),1) == SA[4/5,3/5]

d,n,V = measure(body,SA[-.75,1],4.) @test d ≈ 0.25 @test n ≈ SA[-3/5, 4/5] @test V ≈ SA[-4/5,-3/5] ```
