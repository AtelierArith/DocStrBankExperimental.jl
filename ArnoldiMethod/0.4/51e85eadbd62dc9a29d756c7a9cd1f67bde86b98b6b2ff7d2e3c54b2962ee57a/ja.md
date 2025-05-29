```
ArnoldiWorkspace(n, k) → ArnoldiWorkspace
ArnoldiWorkspace(v1, k) → ArnoldiWorkspace
ArnoldiWorkspace(V, H; V_tmp, Q) → ArnoldiWorkspace
```

アーノルディ関係のための大きな配列を保持します：Vₖ₊₁とHₖは、A * Vₖ = Vₖ₊₁ * Hₖを満たす行列であり、ここでVₖ₊₁はサイズn × (k+1)の直交正規行列であり、Hₖはサイズ(k+1) × kの上ヘッセンベルグ行列です。行列V_tmpとQは再起動に使用され、Vₖ₊₁とHₖと同様のサイズを持ちます（ただしQはk × kであり、k+1 × kではありません）。

## 例

```julia
# 20次元のクリロフ部分空間のためのワークスペースを割り当てる
arnoldi = ArnoldiWorkspace(100, 20)

# 初期ベクトルones(100)をVの最初の列にコピーして、20次元のクリロフ部分空間のためのワークスペースを割り当てる
arnoldi = ArnoldiWorkspace(ones(100), 20)

# V, Hを手動で割り当てる
V = Matrix{Float64}(undef, 100, 21)
H = Matrix{Float64}(undef, 21, 20)
arnoldi = ArnoldiWorkspace(V, H)

# 一時的な配列を含むすべての配列を手動で割り当てる
V, tmp = Matrix{Float64}(undef, 100, 21), Matrix{Float64}(undef, 100, 21)
H, Q = Matrix{Float64}(undef, 21, 20), Matrix{Float64}(undef, 20, 20)
arnoldi = ArnoldiWorkspace(V, H, V_tmp = tmp, Q = Q)
```
