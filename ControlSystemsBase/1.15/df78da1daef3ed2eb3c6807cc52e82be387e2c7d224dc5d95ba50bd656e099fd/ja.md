```
extended_gangoffour(P, C, pos=true)
```

単一の状態空間システムを返し、次のものをマッピングします。

  * `w1` 参照または測定ノイズ
  * `w2` 負荷擾乱

に対して

  * `z1` 制御誤差
  * `z2` 制御入力

```
      z1          z2
      ▲  ┌─────┐  ▲      ┌─────┐
      │  │     │  │      │     │
w1──+─┴─►│  C  ├──┴───+─►│  P  ├─┐
    │    │     │      │  │     │ │
    │    └─────┘      │  └─────┘ │
    │                 w2         │
    └────────────────────────────┘
```

返されるシステムは、伝達関数行列を持ちます。

$$
\begin{bmatrix}
I \\ C
\end{bmatrix} (I + PC)^{-1} \begin{bmatrix}
I & P
\end{bmatrix}
$$

またはコードでは

```julia
# SISO P の場合
S  = G[1, 1]
PS = G[1, 2]
CS = G[2, 1]
T  = G[2, 2]

# MIMO P の場合
S  = G[1:P.ny,     1:P.nu]
PS = G[1:P.ny,     P.ny+1:end]
CS = G[P.ny+1:end, 1:P.ny]
T  = G[P.ny+1:end, P.ny+1:end] # 入力補完感度関数
```

ガングオブフォーは次のようにプロットできます。

```julia
Gcl = extended_gangoffour(G, C) # 閉ループシステムを形成
bodeplot(Gcl, lab=["S" "PS" "CS" "T"], plotphase=false) |> display # ガングオブフォーをプロット
```

注意、Gclの最後の入力は`gangoffour2`からの`PS`および`T`伝達関数の負の値です。同じ符号の伝達行列を得るには [`G_PS`](@ref) および [`input_comp_sensitivity`](@ref) と同じ符号を持つようにするには、`extended_gangoffour(P, C, pos=false)`を呼び出します。拡張例については、RobustAndOptimalControl.jlの`glover_mcfarlane`を参照してください。また、RobustAndOptimalControl.jlの`ncfmargin`および`feedback_control`も参照してください。 ```
