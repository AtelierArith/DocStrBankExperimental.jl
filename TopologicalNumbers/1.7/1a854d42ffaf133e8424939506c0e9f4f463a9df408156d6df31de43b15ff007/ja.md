2次元の場合のベリー流束をFukui-Hatsugai-Suzuki法に基づいて計算します [Fukui2005Chern](@cite)。

```
calcBerryFlux(Hamiltonian::Function, n::Vector{Int64}; N::Int=51, gapless::Real=0.0, rounds::Bool=true)
```

引数

  * Hamiltionian::Function: 一次元の波数 `k` を引数とするハミルトニアン行列。
  * n::Vector{Int64}: ベリー流束を計算する際の波数($2\pi n/N$)。
  * N::Int=51: ブリルアンゾーンを離散化する際のメッシュ数。計算の精度を高めるために、`N` は奇数であることが望ましい。
  * gapless::Real: 状態が重複するかどうかを決定する閾値。メッシュを粗くする(`N`)が、`gapless` を増やすことで計算の精度が向上します。
  * rounds::Bool=true: トポロジカル数の値を整数値に丸めるオプション。`true` の場合、トポロジカル数は `Int` 型の値を返し、`false` の場合は `Float` 型の値を返します。

# 定義

$$
n
$$

番目のバンドの波数 $\bm{k}$ におけるベリー流束 $F_{n}(\bm{k})$ は次のように定義されます。

$$
F_{n}(\bm{k})=f_{n}(\bm{k})-df_{n}(\bm{k})
$$

$$
f_{n}(\bm{k})=\frac{1}{2\pi}\mathrm{Im}\left[\mathrm{Log}\left[U_{n,1}(\bm{k})U_{n,2}(\bm{k}+\bm{e}_{1})U_{n,1}^{*}(\bm{k}+\bm{e}_{2})U_{n,1}^{*}(\bm{k})\right]\right]
$$

$$
df_{n}(\bm{k})=\frac{1}{2\pi}\mathrm{Im}\left[\mathrm{Log}[U_{n,1}(\bm{k})]+\mathrm{Log}[U_{n,2}(\bm{k}+\bm{e}_{1})]-\mathrm{Log}[U_{n,1}(\bm{k}+\bm{e}_{2})]-\mathrm{Log}[U_{n,1}(\bm{k})]\right]
$$

$$
U_{n,i}(\bm{k})
$$

は波数 $\bm{k}$ におけるリンク変数です。$\bm{e}_{i}$ は単位ベクトルです。

$$
U_{n,i}(\bm{k})=\braket{\Psi_{n}(\bm{k})|\Psi_{n}(\bm{k}+\bm{e}_{i})}
$$

$$
\ket{\Psi_{n}(\bm{k})}
$$

は $n$ 番目のバンドの波動関数です。
