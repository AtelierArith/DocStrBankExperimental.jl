```
ghostlayer(forest::Pxest{X}; connection=P4estTypes.CONNECT_FULL(Val(X)))
```

与えられた `forest` に対して、ランクに隣接する象限のゴーストレイヤーを構築します。ここで `connection` は、含める隣接象限を決定します（面、エッジ、コーナー、またはフル）であり、次の値を取ることができます：

  * `P4estTypes.CONNECT_FULL(Val(4))`: 面とコーナーの隣接を取得します。
  * `P4estTypes.CONNECT_FULL(Val(8))`: 面、エッジ、およびコーナーの隣接を取得します。
  * `P4estTypes.CONNECT_FACE(Val(4))`: 面の隣接を取得します。
  * `P4estTypes.CONNECT_FACE(Val(8))`: 面の隣接を取得します。
  * `P4estTypes.CONNECT_EDGE(Val(8))`: 面とエッジの隣接を取得します。
  * `P4estTypes.CONNECT_CORNER(Val(4))`: 面とコーナーの隣接を取得します。
  * `P4estTypes.CONNECT_CORNER(Val(8)):`面、エッジ、およびコーナーの隣接を取得します。
