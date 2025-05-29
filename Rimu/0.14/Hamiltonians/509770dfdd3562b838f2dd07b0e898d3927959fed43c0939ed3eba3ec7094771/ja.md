```
Transcorrelated1D(address; t=1.0, v=1.0, v_ho=0.0, cutoff=1, three_body_term=true)
```

1次元運動量空間における接触相互作用のためのトランスコリレートハミルトニアンを[Jeszenski *et al.* (2018)](http://arxiv.org/abs/1806.11268)に基づいて実装します。現在、2成分フェルミオンアドレスに制限されています。

$$
\begin{aligned}

\tilde{H} &= t \sum_{kσ}k^2 n_{k,σ} \\
    &\quad + \sum_{pqkσσ'} T_{pqk} a^†_{p-k,σ} a^†_{q+k,σ'} a_{q,σ'} a_{p,σ} \\
    &\quad + \sum_{pqskk'σσ'} Q_{kk'}a^†_{p-k,σ} a^†_{q+k,σ} a^†_{s+k-k',σ'}
                                       a_{s,σ'} a_{q,σ} a_{p,σ} \\
    &\quad + V̂_\mathrm{ho}
\end{aligned}
$$

ここで

$$
\begin{aligned}
\tilde{u}(k) &= \begin{cases} -\frac{2}{k^2} &\mathrm{if\ } |k| ≥ k_c\\
0 & \mathrm{otherwise}
\end{cases}
\\

T_{pqk} &= \frac{v}{M} + \frac{2v}{M}\left[k^2\tilde{u}(k)
          - (p - q)k\tilde{u}(k)\right] + \frac{2v^2}{t}W(k)\\
W(k) &= \frac{1}{M^2}\sum_{q} (k - q)q\, \tilde{u}(q)\,\tilde{u}(k - q) \\
Q_{kl} &= -\frac{v^2}{t M^2}k \tilde{u}(k)\,l\tilde{u}(l),
\end{aligned}
$$

# 引数

  * `address`: 開始アドレス、粒子数とサイト数を定義します。
  * `v`: 相互作用パラメータ。
  * `t`: 運動エネルギーの前因子。
  * `v_ho`: 外部調和振動子ポテンシャル $V̂_\mathrm{ho}$ の強さ。 [`HubbardMom1DEP`](@ref)を参照してください。
  * `cutoff`: 上記の方程式における $k_c$ を制御します。注意: カットオフ以下のオフダイアゴナル要素の生成をスキップすることは実装されていません - 代わりにゼロ値の要素が返されます。
  * `three_body_term`: falseに設定すると、三体励起の生成がスキップされます。注意: 三体項を無効にする場合、最良の結果を得るためにカットオフを高い値に設定する必要があります。

# 参照

  * [`HubbardMom1D`](@ref)
  * [`HubbardMom1DEP`](@ref)

```
