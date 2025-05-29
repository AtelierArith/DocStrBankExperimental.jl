```
moveinput!(mpc::PredictiveController, ry=mpc.estim.model.yop, d=[]; <keyword args>) -> u
```

現在の制御期間の最適な操作入力値 `u` を計算します。

`mpc` [`PredictiveController`](@ref) の最適化問題を解決し、結果 $\mathbf{u}(k)$ を返します。先行するホライズンの原則に従い、アルゴリズムは最適な将来の操作入力 $\mathbf{u}(k+1), \mathbf{u}(k+2), ...$ を破棄します。このメソッドは `mpc` の内部データを変更しますが、`mpc.estim` の状態は変更しません。`moveinput!` の前に [`preparestate!(mpc, ym, d)`](@ref) を呼び出し、後に [`updatestate!(mpc, u, ym, d)`](@ref) を呼び出して `mpc` の状態推定を更新します。セットポイントと測定された外乱のプレビューは、`R̂y`、`R̂u`、および `D̂` のキーワード引数で実装できます。

[`PredictiveController`](@ref) オブジェクトを呼び出すと、このメソッドが呼び出されます。

他に [`LinMPC`](@ref)、[`ExplicitMPC`](@ref)、[`NonLinMPC`](@ref) も参照してください。

# 引数

!!! info
    *`強調`* されたキーワード引数は非Unicodeの代替です。


  * `mpc::PredictiveController` : `mpc` の最適化問題を解決します。
  * `ry=mpc.estim.model.yop` : 現在の出力セットポイント $\mathbf{r_y}(k)$。
  * `d=[]` : 現在の測定された外乱 $\mathbf{d}(k)$。
  * `D̂=repeat(d, mpc.Hp)` または *`Dhat`* : 予測された測定外乱 $\mathbf{D̂}$、デフォルトでは将来にわたって一定、または $\mathbf{d̂}(k+j)=\mathbf{d}(k)$ で $j=1$ から $H_p$ まで。
  * `R̂y=repeat(ry, mpc.Hp)` または *`Rhaty`* : 予測された出力セットポイント $\mathbf{R̂_y}$、デフォルトでは将来にわたって一定、または $\mathbf{r̂_y}(k+j)=\mathbf{r_y}(k)$ で $j=1$ から $H_p$ まで。
  * `R̂u=mpc.Uop` または *`Rhatu`* : 予測された操作入力セットポイント $\mathbf{R̂_u}$、デフォルトでは将来にわたって一定、または $\mathbf{r̂_u}(k+j)=\mathbf{u_{op}}$ で $j=0$ から $H_p-1$ まで。

# 例

```jldoctest
julia> mpc = LinMPC(LinModel(tf(5, [2, 1]), 3), Nwt=[0], Hp=1000, Hc=1);

julia> preparestate!(mpc, [0]); ry = [5];

julia> u = moveinput!(mpc, ry); round.(u, digits=3)
1-element Vector{Float64}:
 1.0
```
