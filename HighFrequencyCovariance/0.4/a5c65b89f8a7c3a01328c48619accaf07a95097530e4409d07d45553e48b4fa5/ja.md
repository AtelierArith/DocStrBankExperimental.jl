```
project_to_S(
    A::Hermitian,
    W_root::Union{Hermitian,Diagonal};
    W_inv_sqrt::Union{Hermitian,Diagonal} = sqrt_psd(inv(W_root^2)),
)

project_to_S(
    A::Diagonal,
    W_root::Union{Hermitian,Diagonal};
    W_inv_sqrt::Union{Hermitian,Diagonal,Missing} = missing,
)
```

これは行列を最も近いpsd行列にマッピングします。`W_root`はpsdエルミート重み行列`W`の主平方根である必要があります。`W_inv_sqrt`は`W`の逆の対応する平方根である必要があります。`nearest_psd_matrix`はこの関数のより簡単なインターフェースですが、重み行列を指定することはできません。

### 入力

  * `A` - S空間に投影したい行列。これは`Diagonal`または`Hermitian`であることができます。`Diagonal`行列を入力した場合、それはすでにS空間にあるため、計算なしで返されます。
  * `W_root` - 逆重み行列。
  * `W_inv_sqrt` - `W_root`の平方根。これを持っていない場合は計算されますが、すでに持っている場合は計算の手間を省くことができます。

### 出力

  * `Hermitian`。

### 参考文献

Higham, N. J. 2001. Theorem 3.2
