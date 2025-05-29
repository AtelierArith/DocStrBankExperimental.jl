2次元の場合の最初のチェルン数をFukui-Hatsugai-Suzuki法に基づいて計算します [Fukui2005Chern](@cite)。

```
calcChern(Hamiltonian::Function; N::Int=51, gapless::Real=0.0, rounds::Bool=true)
```

引数

  * Hamiltionian::Function: 2次元の波数 `k` を引数とするハミルトニアン行列。
  * N::Int=51: ブリルアンゾーンを離散化する際のメッシュの数。計算の精度を高めるために、`N` は奇数であることが望ましい。
  * gapless::Real: 状態が重複するかどうかを決定する閾値。メッシュ(`N`)を粗くしつつ `gapless` を増やすことで、計算の精度が向上します。
  * rounds::Bool=true: トポロジカル数の値を整数値に丸めるオプション。`true` の場合、トポロジカル数は `Int` 型の値を返し、`false` の場合は `Float` 型の値を返します。

# 定義

$$
n
$$

番目のバンドの最初のチェルン数 $\nu_{n}$ は次のように定義されます。

$$
\nu_{n}=\frac{1}{2\pi}\sum_{\bm{k}\in\mathrm{BZ}}\mathrm{Im}\left[\mathrm{Log}\left[U_{n,1}(\bm{k})U_{n,2}(\bm{k}+\bm{e}_{1})U_{n,1}^{*}(\bm{k}+\bm{e}_{2})U_{n,2}^{*}(\bm{k})\right]\right]
$$

範囲 $\mathrm{BZ}$(ブリルアンゾーン) は $\bm{k}\in[0,2\pi]^{2}$ です。$U_{n,i}(\bm{k})$ は波数 $\bm{k}$ におけるリンク変数です。$\bm{e}_{i}$ は単位ベクトルです。

$$
U_{n,i}(\bm{k})=\braket{\Psi_{n}(\bm{k})|\Psi_{n}(\bm{k}+\bm{e}_{i})}
$$

$$
\ket{\Psi_{n}(\bm{k})}
$$

は $n$ 番目のバンドの波動関数です。
