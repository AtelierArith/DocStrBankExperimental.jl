```julia
breaction!(
    f,
    u,
    bnode,
    data,
    _::Type{ChargeTransport.OhmicContactRobin}
)

```

ペナルティパラメータ $\delta$ を用いたオーム境界条件を作成します。例えば、静電ポテンシャル $\psi$ の右辺は次のように実装されます。

$$
f[\psi]  = -q/\delta   ( (p - N_a) - (n - N_d) )
$$

、

双極性半導体を仮定しています。一般に、与えられた電荷数 $z_\alpha$ に対して

$$
f[\psi] =  -q/\delta  \sum_\alpha{ z_\alpha  (n_\alpha - C_\alpha) },
$$

ここで $C_\alpha$ は種 $\alpha$ に対するドーピングに対応します。

電子とホールの境界条件はディリクレ条件であり、

$$
\varphi_{\alpha} = U
$$

で、$U$ は印加電圧です。
