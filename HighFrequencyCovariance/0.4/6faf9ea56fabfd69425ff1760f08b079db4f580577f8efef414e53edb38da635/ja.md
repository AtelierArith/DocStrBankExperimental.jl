```
iterate_higham(
   Y::Union{Hermitian,Diagonal},
   Dykstra::Union{Hermitian,Diagonal},
   W_root::Union{Hermitian,Diagonal},
   W_inv::Union{Hermitian,Diagonal},
   W_inv_sqrt::Union{Hermitian,Diagonal},
)
```

入力行列をS空間（psd行列の空間）にマッピングし、その後U空間（単位対角で他のすべてのエントリが絶対値で1未満）にマッピングする1回の反復を行います。更新された行列と次の反復のDykstra補正を返します。

### 入力

  * `Y` - 有効な相関行列の空間に向けて投影したい行列。
  * `Dykstra` - Dykstra補正行列。
  * `W_root` - `W`の平方根。
  * `W_inv` - `W`の逆行列。
  * `W_inv_sqrt` - `W`の逆の平方根。

### 出力

  * `Hermitian`。
  * 更新されたDykstra補正行列。

### 参考文献

Higham, N. J. 2001. Algorithm 3.3
