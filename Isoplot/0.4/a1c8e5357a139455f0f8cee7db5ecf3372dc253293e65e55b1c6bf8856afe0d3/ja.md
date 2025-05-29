```
struct UPbAnalysis{T} <: NoInitialDaughterAnalysis{T}
```

U-Pb分析のコアタイプ。フィールドを持つAnalysisオブジェクトをラップします。

```
μ :: SVector{T<:AbstractFloat}
σ :: SVector{T<:AbstractFloat}
Σ :: SMatrix{T<:AbstractFloat}
```

ここで、`μ`は平均を含みます。

```
μ = [r²⁰⁷Pb²³⁵U, r²⁰⁶Pb²³⁸U]
```

`σ`は標準偏差を含みます。

```
σ = [σ²⁰⁷Pb²³⁵U, σ²⁰⁶Pb²³⁸U]
```

そしてΣは共分散行列を含みます。

```
Σ = [σ₇_₅^2 σ₇_₅*σ₃_₈
     σ₇_₅*σ₃_₈ σ₃_₈^2]
```

`σ`が提供されていない場合、`σ.^2 = diag(Σ)`が成り立つことから、`Σ`から自動的に計算されます。
