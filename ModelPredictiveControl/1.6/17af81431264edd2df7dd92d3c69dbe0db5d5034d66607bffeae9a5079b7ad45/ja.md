```
getinfo(mpc::PredictiveController) -> info
```

`mpc` [`PredictiveController`](@ref) の最適値に関する追加情報を取得します。

この関数は、[`moveinput!`](@ref) を呼び出した後に呼び出す必要があります。次のフィールドを持つ辞書 `info` を返します：

!!! info
    *`強調`* で示されたフィールドは、非Unicodeの代替です。


  * `:ΔU` または *`:DeltaU`* : $H_c$ における最適な操作入力の増分、$\mathbf{ΔU}$
  * `:ϵ` または *`:epsilon`* : 最適なスラック変数、$ϵ$
  * `:D̂` または *`:Dhat`* : $H_p$ における予測された測定外乱、$\mathbf{D̂}$
  * `:ŷ` または *`:yhat`* : 現在の推定出力、$\mathbf{ŷ}(k)$
  * `:Ŷ` または *`:Yhat`* : $H_p$ における最適な予測出力、$\mathbf{Ŷ}$
  * `:Ŷs` または *`:Yhats`* : [`InternalModel`](@ref) の $H_p$ における予測された確率的出力、$\mathbf{Ŷ_s}$
  * `:R̂y` または *`:Rhaty`* : $H_p$ における予測出力セットポイント、$\mathbf{R̂_y}$
  * `:R̂u` または *`:Rhatu`* : $H_p$ における予測操作入力セットポイント、$\mathbf{R̂_u}$
  * `:x̂end` または *`:xhatend`* : 最適な終端状態、$\mathbf{x̂}_i(k+H_p)$
  * `:J`   : 目的値の最適値、$J$
  * `:U`   : $H_p$ における最適な操作入力、$\mathbf{U}$
  * `:u`   : 現在の最適な操作入力、$\mathbf{u}(k)$
  * `:d`   : 現在の測定外乱、$\mathbf{d}(k)$

[`LinMPC`](@ref) および [`NonLinMPC`](@ref) の場合、フィールド `:sol` には印刷可能な最適化ソリューションの概要も含まれています。最後に、経済的コスト `:JE` とカスタム非線形制約 `:gc` の値が最適値で利用可能です [`NonLinMPC`](@ref)。

# 例

```jldoctest
julia> mpc = LinMPC(LinModel(tf(5, [2, 1]), 3), Nwt=[0], Hp=1, Hc=1);

julia> preparestate!(mpc, [0]); u = moveinput!(mpc, [10]);

julia> round.(getinfo(mpc)[:Ŷ], digits=3)
1-element Vector{Float64}:
 10.0
```
