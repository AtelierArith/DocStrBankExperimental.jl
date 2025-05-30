```julia
MagnusGauss4(; krylov = false,
               m = 30,
               iop = 0)
```

半線形ODEソルバー 第4次マグナス法は、2段階ガウス数値積分を使用して近似されます。

### キーワード引数

  * `krylov`: Krylov近似または演算子キャッシングが使用されるかどうかを決定します。後者は半線形問題にのみ利用可能です。 `krylov=true`は大規模なシステムに対してはるかに高速であり、したがってODEが100以上ある場合は推奨されます。
  * `m`: Krylov部分空間のサイズを制御します。
  * `iop`: 0でない場合、不完全直交化手続き（IOP）の長さを決定します。線形演算子/ヤコビアンがエルミートの場合、ランツォスアルゴリズムが常に使用され、IOP設定は無視されることに注意してください。

## 参考文献

@article{hairer2011solving,   title={Solving differential equations on manifolds},   author={Hairer, Ernst},   journal={Lecture notes},   year={2011} }
