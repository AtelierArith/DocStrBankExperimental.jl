MonteCarloは、GeometryBasics basicsで定義された形状をサンプル構築メカニズムの基盤として使用します。しかし、GeometryBasics basicsはすべての必要なメソッドを提供しているわけではありません。追加の3つのメソッドは次のとおりです。

```
isinside(r::Shape, pos::Position)
```

`pos`は`r`の内部に厳密にありますか？

```
intersection(r::Shape, pos0::Particle, pos1::Particle)::Float64
```

`pos0`から`pos1`までの距離のうち、最初に`Shape` `r`と交差する部分を表す数値`f`を返します。交差点は`pos0 .+ f*(pos1 .- pos0)`に等しくなります。`f`が0.0と1.0の間であれば、交差は`pos0`と`pos1`の間の区間にあります。`pos0`から`pos2`に向かう光線が`r`と交差しない場合、この関数はInf64を返します。
