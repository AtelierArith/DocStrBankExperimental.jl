```
FrameBuffer{T}
```

画像用のバッファで、このタイプは第三次元に沿った効率的な更新と統計の計算をサポートします。

次のように構築します：     fb = FrameBuffer(img::Matrix, n)     fb = FrameBuffer{T}(w::Int,h::Int,n::Int)

ここで `n` はバッファの容量です。`fb` は `push!, median, mean, sum, var, std, reshape, size, length, capacity, Matrix, isready` および反復をサポートします。
