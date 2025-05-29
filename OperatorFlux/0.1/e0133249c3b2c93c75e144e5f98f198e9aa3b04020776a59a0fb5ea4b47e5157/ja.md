```
ChebyshevTransform(; modes)
```

モード `modes` を持つ離散チェビシェフ変換を構築し、データの2次元目、3次元目、...N-modes+1次元目で動作します。入力は偶数サイズでなければなりません。

# 例

```
julia> ChebyshevTransform(modes = (12, 3, 4, 12))
```
