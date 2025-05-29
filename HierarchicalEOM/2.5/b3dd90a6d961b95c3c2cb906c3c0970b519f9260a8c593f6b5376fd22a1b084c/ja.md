```
addBosonDissipator(M, jumpOP)
```

与えられたHEOMLS行列にボソニック消散器を追加します。この行列は、システムが追加のボソニック環境と消散的に相互作用する様子を記述します。消散器は次のように定義されます。

$$
D[J](\cdot) = J(\cdot) J^\dagger - \frac{1}{2}\left(J^\dagger J (\cdot) + (\cdot) J^\dagger J \right),
$$

ここで、$J\equiv \sqrt{\gamma}V$はジャンプ演算子、$V$は動力学の消散部分（演算子）を記述し、$\gamma$は非負の減衰率を表し、$[\cdot, \cdot]_+$は反交換子を表します。

$$
V
$$

がフェルミオン系に作用する場合、電荷保存と互換性を持つために偶数パリティである必要があることに注意してください。

# パラメータ

  * `M::AbstractHEOMLSMatrix` : HEOMモデルから与えられた行列
  * `jumpOP::AbstractVector` : 追加する崩壊（ジャンプ）演算子のリスト $\{J_i\}_i$。デフォルトは空のベクトル `[]` です。

# 戻り値

  * `M_new::AbstractHEOMLSMatrix` : 新しいHEOMリウビリアン超演算子行列
