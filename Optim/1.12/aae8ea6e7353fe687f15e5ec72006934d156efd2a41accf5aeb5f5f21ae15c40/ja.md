# SAMIN

## コンストラクタ

```julia
SAMIN(; nt::Int = 5     # nt*ns*dim(x_init) 評価ごとに温度を下げる
        ns::Int = 5     # ns*dim(x_init) 評価ごとに境界を調整する
        t0::T = 2.0     # 初期温度
        rt::T = 0.9     # 幾何学的温度減少係数: 温度が変化するとき、新しい温度は t=rt*t
        r_expand::T = 10.0 # 低カバレッジの状況での幾何学的温度促進係数: 温度が変化するとき、新しい温度は t=r_expand*t
        bounds_ratio::T = 0.6 # 境界増加のカットオフ (1-bounds_ratio は減少のため)
        neps::Int = 5   # 最終結果が比較される以前の最良値の数
        coverage_ok::Bool = false, # false の場合、初期パラメータ空間がカバーされるまで温度を上げる
        verbosity::Int = 1) # スカラー: 0, 1, 2 または 3 (デフォルト = 1).
```

## 説明

`SAMIN` メソッドは、Goffe et. al. (1994) および Goffe (1996) で説明されている境界制約のある問題に対するシミュレーテッドアニーリングアルゴリズムを実装しています。このアルゴリズム

## 参考文献

  * Goffe, et. al. (1994) "Global Optimization of Statistical Functions with Simulated Annealing", Journal of Econometrics, V. 60, N. 1/2.
  * Goffe, William L. (1996) "SIMANN: A Global Optimization Algorithm using Simulated Annealing " Studies in Nonlinear Dynamics & Econometrics, Oct96, Vol. 1 Issue 3.
