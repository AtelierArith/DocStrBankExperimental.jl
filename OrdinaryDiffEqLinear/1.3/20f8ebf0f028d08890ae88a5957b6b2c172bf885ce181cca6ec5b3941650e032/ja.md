```julia
RKMK4(; krylov = false,
        m = 30,
        iop = 0)
```

半線形ODEソルバー 第4次ルンゲ–クッタ–ムンテ–カース法。

### キーワード引数

  * `krylov`: Krylov近似または演算子キャッシングが使用されるかどうかを決定します。後者は半線形問題にのみ利用可能です。`krylov=true`は大規模なシステムに対してはるかに高速であり、したがってODEが100以上ある場合は推奨されます。
  * `m`: Krylov部分空間のサイズを制御します。
  * `iop`: ゼロでない場合、不完全直交化手続き（IOP）の長さを決定します。線形演算子/ヤコビ行列がエルミートの場合、ランツォスアルゴリズムが常に使用され、IOP設定は無視されることに注意してください。

## 参考文献

@article{celledoni2014introduction,   title={Lie群積分法への入門–基本、最新の発展と応用},   author={Celledoni, Elena and Marthinsen, H{a}kon and Owren, Brynjulf},   journal={計算物理学ジャーナル},   volume={257},   pages={1040–1061},   year={2014},   publisher={エルゼビア} }
