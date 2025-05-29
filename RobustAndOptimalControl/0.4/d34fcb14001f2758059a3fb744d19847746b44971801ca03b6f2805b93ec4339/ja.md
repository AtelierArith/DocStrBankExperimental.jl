```
∇A, ∇B, ∇C, ∇D, hn, ω = hinfgrad(sys; rtolinf=1e-8, kwargs...)
∇A, ∇B, ∇C, ∇D        = hinfgrad(sys, hn, ω)
```

状態空間行列 `A,B,C,D` に関する H∞ ノルムの勾配を計算します。システムのみが提供される場合、ノルム `hn` とピーク周波数 `ω` は自動的に計算されます。`kwargs` は [`hinfnorm2`](@ref) に送信されます。ノルムが計算されるデフォルトの許容誤差は、[`hinfnorm2`](@ref) のデフォルトよりも小さく設定されており、勾配は有限でない許容誤差では不連続になり、敏感な最適化アルゴリズムはさらに厳しい許容誤差を必要とする場合があります。

最大特異値が複数の周波数で達成される場合は、ランダムな周波数が使用されます。

システムが不安定な場合、勾配は `NaN` になります。初期安定化コントローラを見つけるための戦略は、Apkarian と D. Noll の "Nonsmooth H∞ Synthesis" において IEEE Transactions on Automatic Control で概説されています。

この関数を使用して ChainRules のための `rrule` が定義されているため、`hn` は ChainRules からルールを導出する任意の AD パッケージで微分可能です（`ω` には適用されません）。
