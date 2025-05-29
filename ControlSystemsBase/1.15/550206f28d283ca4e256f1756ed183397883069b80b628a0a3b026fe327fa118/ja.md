```
add_output(sys::AbstractStateSpace, C2::AbstractArray, D2 = 0)
```

`sys`に出力を追加するには、次のように形成します。

$$
\begin{aligned}
x' &= Ax + Bu \\
y  &= [C; C_2]x + [D; D_2]u \\
\end{aligned}
$$

`C2`が整数の場合、それはインデックスとして解釈され、指定されたインデックスに1が1つだけ含まれる出力行列が使用されます。

`C2 = I(sys.nx)`で呼び出されると、この関数は一部の設定では`augstate`として知られています。
