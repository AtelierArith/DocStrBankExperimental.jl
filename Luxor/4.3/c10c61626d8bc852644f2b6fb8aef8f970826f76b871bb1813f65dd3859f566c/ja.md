```
makebezierpath(pgon::Vector{Point};
    smoothing=1.0)
```

ポリゴン（ポイントの配列）を表すBézierパス（BezierPath）を返します。Bézierパスはセグメントの配列（4つのポイントのタプル）であり、各セグメントは全体のBézierパスの一部を構成する4つのポイントを含みます。

`smoothing`は曲線がポリゴンにどれだけ密接に従うかを決定します。0の値は直線的なパスを返し、1を超える値ではパスが元のポリゴンのエッジからさらに逸脱します。
