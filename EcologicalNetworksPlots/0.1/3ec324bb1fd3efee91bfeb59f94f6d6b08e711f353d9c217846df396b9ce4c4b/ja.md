```
ForceDirectedLayout
```

フィールドは、順番に次のとおりです：

  * `move`、x軸とy軸の移動が許可されているかどうかを指定するタプル
  * `k`、引力と反発の強さを与えるタプル (kₐ,kᵣ)
  * `exponents`、引力と反発関数の指数を与えるタプル (a,b,c,d)
  * `gravity`、中心に向かう引力の強さ、デフォルトは `0.0`
  * `δ`、相互作用の強さの引力を調整する浮動小数点定数 – デフォルト値の0.0に設定されている場合、すべてのエッジは同じ引力を持つ
  * `degree`、ノードがその次数に応じて互いに反発するかどうかを指定するブール値

さまざまな係数は、ノードがどれだけ*引き寄せ*たり*反発*したりするかを、距離Δの関数として決定するために使用されます。具体的には、デフォルトでは接続されたノードは(Δᵃ)×(kₐᵇ)に比例して互いに引き寄せ合い、a=2およびb=-1であり、すべてのノードは(Δᶜ)×(kᵣᵈ)に比例して互いに反発し、c=-1およびd=2です。

Fruchterman-Rheingoldレイアウトのパラメータ化はデフォルトのものであり、特にkₐ=kᵣの場合です。Force Atlas 2のパラメータはkₐ=1（またはb=0）、kᵣは任意の値に設定され、a=1、c=-1、d=1です。すべての場合において、重力は結果の引力の定数倍であるため、これらの選択に敏感であることに注意してください。`FruchtermanRheingold`および`ForceAtlas2`関数は`ForceDirectedLayout`を返します – このオブジェクトは可変であるため、いつでも指数を置き換えることができます。

δパラメータは特に確率的ネットワークにとって重要であり、これらは*すべて*の相互作用が非ゼロの値に設定される傾向があります。そのため、δ=1の値を設定すると、相互作用はその確率に応じてのみ引き寄せ合います。
