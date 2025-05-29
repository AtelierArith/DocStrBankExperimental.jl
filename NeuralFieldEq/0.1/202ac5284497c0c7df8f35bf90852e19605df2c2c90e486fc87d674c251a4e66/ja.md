```
probNFE(neuralFieldEquation)
```

`solveNFE`によって計算されるように神経場方程式を前処理します。

`probNFE`は、`Input1D`および`Input2D`構造体でラップされたパラメータと関数を入力として受け取ります。

# 例

```julia-repl
julia> # 2Dの例
julia> I(x,y,t) = 1                      # 外部入力
julia> K(x,y)   = exp(-x^2+y^2)          # 接続関数
julia> S(V)     = convert(Float64,V>0.0) # 発火率。ヘイシード関数 H(V)

julia> α  = 1.0  # 定数減衰
julia> v  = 20.0 # 有限軸索速度
julia> V0 = 0.0  # 初期条件
julia> L  = 100  # ドメインの長さ
julia> N  = 512  # 空間を離散化するノードの数
julia> T  = 20.0 # 時間の範囲
julia> n  = 200  # 時間を離散化するノードの数

julia> nf   = Input2D(α,v,V0,L,N,T,n,I,K,S);
julia> prob = probNFE(nf)
├─ ドメイン:       Ω × [0,T] = [-50.0,49.8046875]^2 × [0,20.0]
├─ 空間ステップ: dx   = 0.1953125
├─ 時間ステップ: dt   = 0.1
├─ 速度:         v    = 20.0
├─ 遅延リング:    umax = 36
```

1Dドメインの場合も手順は同じですが、入力は`Input1D`を使用してラップされます。
