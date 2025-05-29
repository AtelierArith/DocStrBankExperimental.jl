```
SARIMA(
    y::Vector{Fl}; 
    order::Tuple{Int,Int,Int} = (1, 0, 0), 
    seasonal_order::Tuple{Int, Int, Int, Int} = (0, 0, 0, 0),
    include_mean::Bool = false,
    suppress_warns::Bool = false
) where Fl
```

状態空間フレームワーク内で実装されたSARIMAモデル（季節自己回帰統合移動平均）。

SARIMAモデルは$(p, d, q) \times (P, D, Q, s)$として指定されます。また、トレンドをモデル化するための多項式$A(t)$を考慮することもできますが、ここでは`include_mean`キーワード引数を使用して定数項を追加することのみを許可します。    

$$
\begin{gather*}
    \begin{aligned}
        \phi_p (L) \tilde \phi_P (L^s) \Delta^d \Delta_s^D y_t = A(t) + \theta_q (L) \tilde \theta_Q (L^s) \zeta_t
    \end{aligned}
\end{gather*}
$$

単変量構造モデルの観点から、これは次のように表現できます。

$$
\begin{gather*}
    \begin{aligned}
    y_t & = u_t + \eta_t \\
    \phi_p (L) \tilde \phi_P (L^s) \Delta^d \Delta_s^D u_t & = A(t) + \theta_q (L) \tilde \theta_Q (L^s) \zeta_t
    \end{aligned}
\end{gather*}
$$

# 例

```jldoctest
julia> model = SARIMA(rand(100); order=(1,1,1), seasonal_order=(1,2,3,12))
SARIMA(1, 1, 1)x(1, 2, 3, 12) with zero mean
```

[航空会社の乗客](@ref)についての詳細

# 参考文献

  * Durbin, James, & Siem Jan Koopman. Time Series Analysis by State Space Methods: Second Edition.  Oxford University Press, 2012
