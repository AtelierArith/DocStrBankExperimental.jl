```
G = feedback_control(P, K)
```

入力 `K` から出力 `P` への（負のフィードバック）閉ループシステムを返し、制御信号（`K` の出力）も出力します。すなわち、`G` は参照を `[y; u]` にマッピングします。

# 例:

以下は同じことを達成するための2つの同等の方法です。

```julia
G = ssrand(3,4,2)
K = ssrand(4,3,2)

Gcl1 = feedback_control(G, K) # 最初のオプション

# 名前付きシステムと接続を使用した2番目のオプション
G = named_ss(G, :G)
K = named_ss(K, :K)
S = sumblock("Ku = r - Gy", n=3) # ベクトルの長さ3のために r - Gy を計算するサムブロックを作成

z1 = [G.y; K.y] # プラントとコントローラの出力の両方を出力
w1 = :r^3       # 外部入力はサムブロックへの3つの参照
connections = [K.y .=> G.u; G.y .=> G.y; K.u .=> K.u] # サムブロックが G,K の IO 信号と同じ名前を使用しているため、ここでこれらの名前を再利用できます
Gcl2 = connect([G, K, S], connections; z1, w1)

@test linfnorm(minreal(Gcl1 - Gcl2.sys))[1] < 1e-10 # 同じです
```

入力の外乱も含めるには、次のようにします。

```
Gcl = feedback(K, P, W2=:, Z2=:, Zperm=[(1:ny).+nu; 1:nu]) # y,u from r,d
```

[`extended_gangoffour`](@ref) も参照してください。
