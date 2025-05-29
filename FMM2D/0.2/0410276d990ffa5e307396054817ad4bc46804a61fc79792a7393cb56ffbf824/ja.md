```julia
    vals = lfmm2d(eps,zk,sources;
            charges=nothing,dipstr=nothing,dipvecs=nothing,targets=nothing,pg=0,pgt=0,nd=1)
```

このサブルーチンは、相互作用カーネルが log(r) とその勾配である二次元の N-body ラプラス相互作用を計算します。

$$
    u(x) = \sum_{j=1}^{N} c_{j} * log\(\|x-x_{j}\|\) - d_{j}v_{j} \cdot \nabla( log(\|x-x_{j}\|) ),
$$

ここで、$c_{j}$ は電荷密度、$d_{j}$ は双極子強度ベクトル、$v_{j}$ は双極子方向ベクトル、$x_{j}$ はソースの位置です。$x=x_{j}$ のとき、j 番目の項は合計から除外されます。

# 入力

  * `eps::Float64` 要求される精度
  * `sources::Array{Float64}` サイズ (2,n) ソースの位置 ($x_{j}$)

# オプションのキーワード入力

  * `charges::Array{ComplexF64}` サイズ (nd,n)
  * `dipstr::Array{ComplexF64}`  サイズ (nd,n)
  * `dipvecs::Array{Float64}` サイズ (nd,2,n) または (2,n) 双極子方向ベクトル ($d_{j}$)
  * `targets::Array{Float64}` サイズ (2,nt) ターゲットの位置 ($x$)
  * `pg::Integer` ソース評価フラグ。

      * `pg == 0` の場合、ソースでの量は計算しない
      * `pg == 1` の場合、ソースで評価されたポテンシャル ($u$)。
      * `pg == 2` の場合、ソースで評価されたポテンシャルと勾配 ($\nabla u$)
      * `pg == 3` の場合、ソースで評価されたポテンシャル、勾配、およびヘッセ行列 ($\nabla \nabla u$)
  * `pgt::Integer` ターゲット評価フラグ。

      * `pgt == 0` の場合、ターゲットでの量は計算しない
      * `pgt == 1` の場合、ターゲットで評価されたポテンシャル。
      * `pgt == 2` の場合、ターゲットで評価されたポテンシャルと勾配
      * `pgt == 3` の場合、ターゲットで評価されたポテンシャル、勾配、およびヘッセ行列
  * `nd::Integer` 密度の数

注意: オプション入力にすべてのデフォルト値が使用される場合、何も計算されません。

# 出力

`vals::FMMVals` フィールドを持ち、ヘッセ行列は各点で長さ 4 のベクトルとして返され、二次導関数は次の順序で配置されます: $\partial_{xx}$, $\partial_{yy}$, $\partial_{xy}$, $\partial_{yx}$。

  * `vals.pot::Array{ComplexF64}` サイズ (nd,n) または (n) 要求されたソース位置でのポテンシャル
  * `vals.grad::Array{ComplexF64}` サイズ (nd,2,n) または (2,n) 要求されたソース位置での勾配
  * `vals.hess::Array{ComplexF64}` サイズ (nd,3,n) または (3,n) 要求されたソース位置でのヘッセ行列
  * `vals.pottarg::Array{ComplexF64}` サイズ (nd,nt) または (nt) 要求されたターゲット位置でのポテンシャル
  * `vals.gradtarg::Array{ComplexF64}` サイズ (nd,2,nt) または (2,nt) 要求されたターゲット位置での勾配
  * `vals.hesstarg::Array{ComplexF64}` サイズ (nd,3,nt) または (3,nt) 要求されたターゲット位置でのヘッセ行列
  * `vals.ier` FMM2D ライブラリによって返されるエラーフラグ。値が 0 の場合、呼び出しが成功したことを示します。

非ゼロの値は、利用可能なメモリが不足していることを示す場合があります。FMM2D ライブラリのドキュメントを参照してください。設定されていない場合（`nothing`）、FMM2D ライブラリは呼び出されていませんでした。
