```
getinfo(estim::MovingHorizonEstimator) -> info
```

`estim` [`MovingHorizonEstimator`](@ref) の最適値に関する追加情報を取得します。

`estim.direct==true` の場合、[`preparestate!`](@ref) を呼び出した後にこの関数を呼び出す必要があります。それ以外の場合は、[`updatestate!`](@ref) の後に呼び出してください。次のフィールドを持つ辞書 `info` を返します：

!!! info
    *`強調`* 付きのフィールドは非Unicodeの代替です。


  * `:Ŵ` または *`:What`* : $N_k$ における最適推定プロセスノイズ、$\mathbf{Ŵ}$
  * `:ϵ` または *`:epsilon`* : 最適スラック変数、$ϵ$
  * `:X̂` または *`:Xhat`* : $N_k+1$ における最適推定状態、$\mathbf{X̂}$
  * `:x̂` または *`:xhat`* : 最適推定状態、$\mathbf{x̂}_k(k+p)$
  * `:V̂` または *`:Vhat`* : $N_k$ における最適推定センサーノイズ、$\mathbf{V̂}$
  * `:P̄` または *`:Pbar`* : 到着時の推定誤差共分散、$\mathbf{P̄}$
  * `:x̄` または *`:xbar`* : 到着時の最適推定誤差、$\mathbf{x̄}$
  * `:Ŷ` または *`:Yhat`* : $N_k$ における最適推定出力、$\mathbf{Ŷ}$
  * `:Ŷm` または *`:Yhatm`* : $N_k$ における最適推定測定出力、$\mathbf{Ŷ^m}$
  * `:x̂arr` または *`:xhatarr`* : 到着時の最適推定状態、$\mathbf{x̂}_k(k-N_k+p)$
  * `:J`   : 目的関数の最適値、$J$
  * `:Ym`  : $N_k$ における測定出力、$\mathbf{Y^m}$
  * `:U`   : $N_k$ における操作入力、$\mathbf{U}$
  * `:D`   : $N_k$ における測定外乱、$\mathbf{D}$
  * `:sol` : 印刷用の最適化器の解の要約

# 例

```jldoctest
julia> model = LinModel(ss(1.0, 1.0, 1.0, 0, 5.0));

julia> estim = MovingHorizonEstimator(model, He=1, nint_ym=0, direct=false);

julia> updatestate!(estim, [0], [1]);

julia> round.(getinfo(estim)[:Ŷ], digits=3)
1-element Vector{Float64}:
 0.5
```
