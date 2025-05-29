```
mother(this::CWT{W, T, <:ContWaveClass, N}, s::Real, nInOctave::Int,
    ω::AbstractArray{<:Real,1}) where {W, T, N} -> daughter
```

CWTオブジェクトを与えられた場合、フーリエ領域で母波レットの再スケーリングされたバージョンを返します。ωは周波数で、fftshiftされています。sはスケール変数です。
