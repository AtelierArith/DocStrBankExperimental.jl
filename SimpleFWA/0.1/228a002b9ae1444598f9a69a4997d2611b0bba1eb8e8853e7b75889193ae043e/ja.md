```
simpleFWA( nFireworks::Int,
           nSparks::Int;
           λ_0::Float32,
           ϵ_A::Float32,
           C_a::Float32,
           C_r::Float32,
           lower::Vector{Float32},
           upper::Vector{Float32},
           objFunction::Function,
           XPrimary::Vector{ Matrix{Float32} },
           yPrimary::Vector{ Matrix{Float32} },
           maxiter::Int,
           ϵ_conv::Float32=1f-6 )
目的関数 objFunction を最小化し、解空間は下限と上限によって制限されます。
使用される最適化アルゴリズムは、dynFireWorksAlgorithm の簡略版です。nFireworks
パラメータは、各イテレーションで並行して評価される花火の数を制御します。nSparks は
各花火ごとに一定の火花の数です。ϵ_A は、各 fw に対して計算される振幅の分散を制御する
スムージングパラメータです。C_a は爆発振幅のスケーリングアップパラメータです。C_r は
爆発振幅のスケーリングダウンパラメータです。XPrimary は調整されるプライマリアルゴリズムの
特徴セットです。yPrimary はプライマリアルゴリズムのターゲットセットです。maxiter は
最大イテレーション数です。ϵ_conv は収束パラメータを示します。
```
