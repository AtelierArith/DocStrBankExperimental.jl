```
meander!(p::Path, len, straightlen, r, α)
```

長さ `straightlen` で真っ直ぐ進み、半径 `r` と角度 `α` で曲がることを交互に行います。各ターンは前のターンとは反対の方向に行います。合計の長さは `len` です。共鳴器を作るのに便利です。

直線とターンのセグメントは `CompoundSegment` に結合され、パス `p` に追加されます。
