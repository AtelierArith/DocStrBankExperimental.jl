```
SmootherOutput{T<:Real}
```

Quadratic Kalman Smootherからの出力のコンテナ。この構造体は、過去および未来の観測からの情報を取り入れることによって状態推定を洗練する平滑化アルゴリズムによって生成された結果をカプセル化します。スムーザーは通常、フィルター単独よりもより正確な状態推定と関連する不確実性の定量化を提供します。

# フィールド

  * `Z_smooth::Matrix{T}`: 平滑化された状態推定を含む行列。行列の次元はP × (T̄+1)であり、ここでPは状態ベクトルの次元、T̄+1は時間ステップの数を示します。
  * `P_smooth::Array{T,3}`: 平滑化された共分散行列を保持する三次元配列。各スライスP_smooth[:, :, t]は、時間ステップtにおける状態の共分散推定に対応し、全体の次元はP × P × (T̄+1)です。

# 詳細

平滑化された状態と共分散は、Quadratic Kalman Smootherを使用して計算され、これは後方再帰によってフィルタリング結果を向上させます。これにより、過去の測定だけでなく未来の測定も考慮することによって状態推定が改善されます。この構造体は、状態推定の不確実性が重要な役割を果たすアプリケーションにおける診断チェックやその後の分析に不可欠です。
