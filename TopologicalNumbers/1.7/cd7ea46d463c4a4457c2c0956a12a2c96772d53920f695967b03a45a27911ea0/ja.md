```
T, L, P = skew_LTL(A::AbstractMatrix{T}; overwrite_a=false, calc_L=true, calc_P=true) where {T<:Number}
```

実数または複素数の斜め対称行列 (A=-A^T) を、ゼロ対角を持つ三重対角行列 T に変換し、P A P^T= L T L^T となる下三角単位行列 L を得ます。

overwrite*a=true の場合、A は上書きされます (デフォルト: false)。L と P はそれぞれ calc*L=true または calc_P=true の場合のみ計算されます (デフォルト: true)。
