```
PlaneSource(medium::P, amplitude::SVector, direction::SVector)
```

は、全体のシステムを駆動/強制する平面波源を記述する構造体型です。物理的な `medium`、源の `amplitude`、および伝播する方向の `direction` の3つのフィールドがあります。

任意の角周波数 ω に対して、PlaneSource は点 $\mathbf x$ での値 $e^{i ω/c \mathbf v \cdot \mathbf x }$ を持ち、ここで $c$ は媒質の波速、$\mathbf v$ は方向です。
