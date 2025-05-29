```julia
    vals = hfmm2d(eps,zk,sources;
            charges=nothing,dipstr=nothing,dipvecs=nothing,targets=nothing,pg=0,pgt=0,nd=1)
```

この関数は、相互作用カーネルが $H_0^{(1)}(kr)$ とその勾配で与えられる2次元のN体ヘルムホルツ相互作用を計算します。これは、要求された精度で相互作用を計算する $O(N)$ ファスト多重極コードです。

$$
 u(x) = \sum_{j=1}^{N} c_jH_0^{(1)}(k\|x - x_{j}\|) - v_j\mathbf{d}_j\cdot\nabla H_0^{(1)}(k\|x - x_{j}\|),
$$

ここで、$c_{j}$ は電荷密度、$v_{j}$ は双極子強度、$d_{j}$ は双極子の方向ベクトル、$x_{j}$ はソースの位置です。$x=x_{j}$ のとき、j番目の項は合計から除外されます。

# 入力

  * `eps::Float64` 要求された精度
  * `zk::ComplexF64` ヘルムホルツパラメータ
  * `sources::Array{Float64}` サイズ (2,n) ソースの位置 ($x_{j}$)

# オプションのキーワード入力

  * `charges::Array{ComplexF64}` サイズ (nd,n) または (n) 電荷密度 (c_{j})
  * `dipstr::Array{ComplexF64}`  サイズ (nd,n) または (n) 双極子強度 ($v_{j}$)
  * `dipvecs::Array{Float64}` サイズ (nd,2,n) または (2,n) 双極子の方向ベクトル ($d_{j}$)
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

注意: オプション入力のすべてのデフォルト値が使用される場合、何も計算されません。

# 出力

`vals::FMMVals` フィールドを持つことに注意してください。ヘッセ行列は、各点で長さ4のベクトルとして返され、2次導関数は次の順序で配置されます: $\partial_{xx}$, $\partial_{yy}$, $\partial_{xy}$, $\partial_{yx}$。

  * `vals.pot::Array{ComplexF64}` サイズ (nd,n) または (n) 要求された場合のソース位置でのポテンシャル
  * `vals.grad::Array{ComplexF64}` サイズ (nd,2,n) または (2,n) 要求された場合のソース位置での勾配
  * `vals.hess::Array{ComplexF64}` サイズ (nd,4,n) または (4,n) 要求された場合のソース位置でのヘッセ行列
  * `vals.pottarg::Array{ComplexF64}` サイズ (nd,nt) または (nt) 要求された場合のターゲット位置でのポテンシャル
  * `vals.gradtarg::Array{ComplexF64}` サイズ (nd,2,nt) または (2,nt) 要求された場合のターゲット位置での勾配
  * `vals.hesstarg::Array{ComplexF64}` サイズ (nd,4,nt) または (4,nt) 要求された場合のターゲット位置でのヘッセ行列
  * `vals.ier` FMM2Dライブラリによって返されるエラーフラグ。値が0の場合、呼び出しが成功したことを示します。

非ゼロの値は、利用可能なメモリが不足していることを示す場合があります。FMM2Dライブラリのドキュメントを参照してください。設定されていない場合（`nothing`）、FMM2Dライブラリは呼び出されていませんでした。
