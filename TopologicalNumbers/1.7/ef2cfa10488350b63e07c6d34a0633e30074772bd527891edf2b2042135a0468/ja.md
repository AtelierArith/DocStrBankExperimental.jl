一次元の場合の巻数を計算します。

```
calcBerryPhase(Hamiltonian::Function; N::Int=51, gapless::Real=0.0, rounds::Bool=true)
```

引数

  * `Hamiltonian::Function`: 一次元の波数 `k` を引数とするハミルトニアン行列関数。
  * `N::Int`: ブリルアンゾーンを離散化する際のメッシュの数。計算の精度を高めるために、`N` は奇数であることが望ましい。
  * `gapless::Real`: 状態が重複するかどうかを決定する閾値。メッシュ(`N`)を粗くするが `gapless` を増やすことで計算の精度が向上する。
  * `rounds::Bool`: トポロジカル数の値を整数値に丸めるオプション。`true` の場合、トポロジカル数は `Int` 型の値を返し、`false` の場合は `Float` 型の値を返す。

# 定義

$$
n
$$

番目のバンドのベリー位相 $\nu_{n}$ は次のように定義されます。

$$
\nu_{n}=\frac{1}{\pi}\sum_{k\in\mathrm{BZ}}U_{n}(k)
$$

範囲 $\mathrm{BZ}$(ブリルアンゾーン) は $k\in[0,2\pi]$ です。$U_{n,i}(k)$ は波数 $k$ におけるリンク変数です。$e_{1}$ は単位ベクトルです。

$$
U_{n}(k)=\braket{\Psi_{n}(k)|\Psi_{n}(k+e_{1})}
$$

$$
\ket{\Psi_{n}(k)}
$$

は $n$ 番目のバンドの波動関数です。
