```
addFermionDissipator(M, jumpOP)
```

与えられたHEOMLS行列にフェルミオン散逸子を追加します。この行列は、システムが追加のフェルミオン環境と散逸的に相互作用する様子を記述します。`EVEN`パリティを持つ散逸子は次のように定義されます。

$$
D_{\textrm{even}}[J](\cdot) = J(\cdot) J^\dagger - \frac{1}{2}\left(J^\dagger J (\cdot) + (\cdot) J^\dagger J \right),
$$

ここで、$J\equiv \sqrt{\gamma}V$はジャンプ演算子、$V$は動力学の散逸部分（演算子）を表し、$\gamma$は非負の減衰率を表し、$[\cdot, \cdot]_+$は反交換子を表します。

同様に、`ODD`パリティを持つ散逸子は次のように定義されます。

$$
D_{\textrm{odd}}[J](\cdot) = - J(\cdot) J^\dagger - \frac{1}{2}\left(J^\dagger J (\cdot) + (\cdot) J^\dagger J \right),
$$

散逸子のパリティは、与えられたHEOMLS行列`M`のパリティによって決まることに注意してください。

# パラメータ

  * `M::AbstractHEOMLSMatrix` : HEOMモデルから与えられた行列
  * `jumpOP::AbstractVector` : 追加する崩壊（ジャンプ）演算子のリスト。デフォルトは空のベクトル`[]`です。

# 返り値

  * `M_new::AbstractHEOMLSMatrix` : 新しいHEOMリウビリアン超演算子行列

```
