```
Polygon(p::AbstractPath; tol=<default>)
Polygon(p::AbstractVector{<:AbstractCurve}; tol=<default>)
```

(閉じている可能性のある) パスまたは曲線のベクターからポリゴンを構築します。`tol` パラメータは、パスの連続性と閉じているかどうかをチェックする際に使用される許容誤差です。
