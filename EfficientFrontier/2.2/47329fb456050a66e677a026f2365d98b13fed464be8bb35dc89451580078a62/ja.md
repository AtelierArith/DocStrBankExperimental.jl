```
    sCL(P::Problem)         問題 P のための空の sCL 構造体のベクターを定義します

    struct sCL{T<:AbstractFloat}
```

クリティカルラインセグメント、フィールド: デフォルト T = Float64

```
        S::Vector{Status}       # (N+J)x1
        K::Int              # IN 資産の数
        L1::T                   # 高いラムダ
        I1::Vector{Event{T}}    # L1 での入出イベント
        L0::T                   # 低いラムダ
        I0::Vector{Event{T}}    # L0 での入出イベント
        alpha::Vector{T}        # K x 1
        beta::Vector{T}         # K x 1
```
