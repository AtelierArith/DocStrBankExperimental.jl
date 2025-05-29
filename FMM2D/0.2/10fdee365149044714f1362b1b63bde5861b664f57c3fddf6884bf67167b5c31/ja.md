```julia
    vals = cfmm2d(eps,zk,sources;
            charges=nothing,dipstr=nothing,targets=nothing,pg=0,pgt=0,nd=1)
```

このサブルーチンは、相互作用カーネルが log(r) とその勾配である二次元の N体ラプラス相互作用を計算します。

$$
    u(z) = \sum_{j=1}^{N} c_{j} * log\(\|z - \epsilon_j\|\) - \frac{v_j}{z - \epsilon_j},
$$

ここで、$c_{j}$ は電荷の強さ、$v_{j}$ は双極子の強さ、$z_{j} = x_{j}(1) + ix_{j}(2)$ は $x_{j}$ に対応する複素数です。$z=\epsilon_{j}$ のとき、j番目の項は合計から除外されます。

# 入力

  * `eps::Float64` 要求される精度
  * `sources::Array{Float64}` サイズ (2,n) ソース位置 ($x_{j}$)

# オプションのキーワード入力

  * `charges::Array{ComplexF64}` サイズ (nd,n)
  * `dipstr::Array{ComplexF64}`  サイズ (nd,n)
  * `targets::Array{Float64}` サイズ (2,nt) ターゲット位置 ($x$)
  * `pg::Integer` ソース評価フラグ。

      * `pg == 0` の場合、ソースでの量は計算しない
      * `pg == 1` の場合、ソースでのポテンシャル ($u$) が評価される。
      * `pg == 2` の場合、ソースでのポテンシャルと勾配 ($\nabla u$) が評価される
      * `pg == 3` の場合、ソースでのポテンシャル、勾配、およびヘッセ行列 ($\nabla \nabla u$) が評価される
  * `pgt::Integer` ターゲット評価フラグ。

      * `pgt == 0` の場合、ターゲットでの量は計算しない
      * `pgt == 1` の場合、ターゲットでのポテンシャルが評価される。
      * `pgt == 2` の場合、ターゲットでのポテンシャルと勾配が評価される
      * `pgt == 3` の場合、ターゲットでのポテンシャル、勾配、およびヘッセ行列が評価される
  * `nd::Integer` 密度の数

注意: オプション入力のすべてのデフォルト値が使用される場合、何も計算されません。

# 出力

`vals::FMMVals` フィールドを持ち、ヘッセ行列は各点で長さ4のベクトルとして返され、二次導関数は次の順序で配置されます: $\partial_{xx}$, $\partial_{yy}$, $\partial_{xy}$, $\partial_{yx}$。

  * `vals.pot::Array{ComplexF64}` サイズ (nd,n) または (n) 要求された場合のソース位置でのポテンシャル
  * `vals.grad::Array{ComplexF64}` サイズ (nd,2,n) または (2,n) 要求された場合のソース位置での勾配
  * `vals.hess::Array{ComplexF64}` サイズ (nd,3,n) または (3,n) 要求された場合のソース位置でのヘッセ行列
  * `vals.pottarg::Array{ComplexF64}` サイズ (nd,nt) または (nt) 要求された場合のターゲット位置でのポテンシャル
  * `vals.gradtarg::Array{ComplexF64}` サイズ (nd,2,nt) または (2,nt) 要求された場合のターゲット位置での勾配
  * `vals.hesstarg::Array{ComplexF64}` サイズ (nd,3,nt) または (3,nt) 要求された場合のターゲット位置でのヘッセ行列
  * `vals.ier` FMM2Dライブラリによって返されるエラーフラグ。値が0の場合、呼び出しが成功したことを示します。

非ゼロの値は、利用可能なメモリが不足していることを示す場合があります。FMM2Dライブラリのドキュメントを参照してください。設定されていない場合（`nothing`）、FMM2Dライブラリは呼び出されていません。
