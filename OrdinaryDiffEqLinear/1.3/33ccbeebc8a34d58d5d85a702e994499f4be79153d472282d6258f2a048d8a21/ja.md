```julia
MagnusGL6(; krylov = false,
            m = 30,
            iop = 0)
```

半線形ODEソルバー 第六次のマグナス法はガウス・レジャンドル数値積分を用いて近似されます。

### キーワード引数

  * `krylov`: Krylov近似または演算子キャッシングが使用されるかどうかを決定します。後者は半線形問題にのみ利用可能です。`krylov=true`は大規模なシステムに対してはるかに高速であり、したがってODEが100を超える場合は推奨されます。
  * `m`: Krylov部分空間のサイズを制御します。
  * `iop`: ゼロでない場合、不完全直交化手続き（IOP）の長さを決定します。線形演算子/ヤコビアンがエルミートの場合、ランツォスアルゴリズムが常に使用され、IOP設定は無視されることに注意してください。

## 参考文献

@article{blanes2000improved,   title={Improved high order integrators based on the Magnus expansion},   author={Blanes, Sergio and Casas, Fernando and Ros, Javier},   journal={BIT Numerical Mathematics},   volume={40},   number={3},   pages={434–450},   year={2000},   publisher={Springer} }
