```
calculate_limit_gradient(CH::AbstractChart, rl::Real)
calculate_limit_gradient(nominal::ARL, rl)
calculate_limit_gradient(nominal::QRL, rl)
```

制御限界の最適化のための勾配を計算します。

制御チャートの`nominal`属性が`ARL`型の場合、勾配はCapizziとMasarotto（2016）の式（9）に従って計算されます。

制御チャートの`nominal`属性が`QRL`型の場合、勾配はCapizziとMasarotto（2009）の280ページの再帰を使用して計算されます。

### 参考文献

Capizzi, G., & Masarotto, G. (2016). "Efficient Control Chart Calibration by Simulated Stochastic Approximation". IIE Transactions 48 (1). https://doi.org/10.1080/0740817X.2015.1055392.

Capizzi, G. & Masarotto, G. (2009) Bootstrap-based design of residual control charts, IIE Transactions, 41:4, 275-286, DOI: https://doi.org/10.1080/07408170802120059 
