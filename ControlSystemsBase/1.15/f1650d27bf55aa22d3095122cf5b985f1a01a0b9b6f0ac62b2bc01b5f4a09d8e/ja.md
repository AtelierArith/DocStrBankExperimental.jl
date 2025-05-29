```
cont = observer_controller(sys, L::AbstractMatrix, K::AbstractMatrix; direct=false)
```

# `direct = false` の場合

`ss(A - B*L - K*C + K*D*L, K, L, 0)` によって与えられる observer_controller `cont` を返します。このとき、`feedback(sys, cont)` は固有値が `A-KC` と `A-BL` である閉ループシステムを生成します。

このコントローラには直接項がなく、[`observer_predictor`](@ref) によって推定された状態に対して動作する状態フィードバックに対応します。計算された制御信号が次のサンプリング瞬間に適用される場合、またはコントローラに供給される測定値に対して大きな遅延がある場合には、この形式を使用してください。

参照: "Computer-Controlled Systems" Eq 4.37

# `direct = true` の場合

`ss((I-KC)(A-BL), (I-KC)(A-BL)K, L, LK)` によって与えられる observer controller `cont` を返します。このとき、`feedback(sys, cont)` は固有値が `A-BL` と `A-BL-KC` である閉ループシステムを生成します。このコントローラには直接項があり、[`observer_filter`](@ref) によって推定された状態に対して動作する状態フィードバックに対応します。計算された制御信号が測定値を受け取った直後に適用される場合には、この形式を使用してください。このバージョンは通常、直接項のないものよりもパフォーマンスが優れています。

!!! note
    この定式化を使用するには、オブザーバゲイン `K` は `(A, CA)` のペアのために設計されている必要があります。これを行うには、[`place`](@ref) または [`kalman`](@ref) を呼び出す際に `direct = true` を渡してください。


参照: "Computer-Controlled Systems" pp 140 および "Computer-Controlled Systems" pp 162 prob 4.7

# 引数:

  * `sys`: システムのモデル
  * `L`: 状態フィードバックゲイン `u = -Lx`
  * `K`: オブザーバゲイン

[`observer_predictor`](@ref) および [`innovation_form`](@ref) も参照してください。
