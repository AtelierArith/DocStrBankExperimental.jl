```
add_input(sys::AbstractStateSpace, B2::AbstractArray, D2 = 0)
```

`sys`に入力を追加するには、次のように形成します。

$$
\begin{aligned}
x' &= Ax + [B \; B_2]u \\
y  &= Cx + [D \; D_2]u \\
\end{aligned}
$$

`B2`が整数の場合、それはインデックスとして解釈され、指定されたインデックスに1が1つだけ含まれる入力行列が使用されます。

例: 次の例は、イノベーションを入力として受け取るイノベーションモデルを形成します。

```julia
G   = ssrand(2,2,3, Ts=1)
K   = kalman(G, I(G.nx), I(G.ny))
sys = add_input(G, K)
```
