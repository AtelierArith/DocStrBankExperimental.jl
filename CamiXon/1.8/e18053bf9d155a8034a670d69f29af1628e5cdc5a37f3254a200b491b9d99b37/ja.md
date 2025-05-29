```
B_exchange(k::Int, l::Int, l′::Int)
```

シェル平均コロンブ角積分 - 交換部分:

$$
B^{k}(l,l^{\prime})=\frac{1}{w_{l}}\sum_{m_{l}=-l}^{l}b^{k}(lm_{l};l^{\prime}m_{l^{\prime}})=\tfrac{1}{2}\left(\begin{array}{ccc}
l & k & l^{\prime}\\
0 & 0 & 0
\end{array}\right)^{2}
$$

ここで、$w_{l}=2(2l+1)$は閉殻$(nl)^{w_l}$の電子の数です。シェル平均$B^{k}(l,l^{\prime})$は$m_{l^{\prime}}$に*依存しない*ことに注意してください。

#### 例:

```
julia> l = 2; l′= 3; wl = 2(2l+1);

julia> [B_exchange(k, l, l′) for k=0:(l+l′)] == [0, 3//70, 0, 2//105, 0, 5//231]
true

julia> [sum([b_exchange(k, l, ml, l′, 0) for ml=-l:l])//wl for k=0:(l+l′)] == [0, 3//70, 0, 2//105, 0, 5//231]
true
```
