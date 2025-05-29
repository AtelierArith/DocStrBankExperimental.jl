```
`GaussianPolicy{P}`
```

# フィールド:

```
T::Int          # 時間ステップの数
n::Int          # 状態次元
m::Int          # 制御入力の数
K::Array{P,3}   # 時間変化するフィードバックゲイン ∈ R(n,m,T)
k::Array{P,2}   # オープンループ制御信号 ∈ R(m,T)
Σ::Array{P,3}   # 時間変化するコントローラーの共分散 ∈ R(m,m,T)
Σi::Array{P,3}  # Σの逆行列
```
