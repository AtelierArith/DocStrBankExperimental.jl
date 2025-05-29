```
@imagematrix! バッファ 描画指示 [幅=256] [高さ=256]
```

`@imagematrix` と同様ですが、既存の UInt32 バッファを使用します。

```julia
w = 200
h  = 150
buffer = zeros(UInt32, w, h)
m = @imagematrix! buffer juliacircles(40) 200 150;
Images.RGB.(m)
```
