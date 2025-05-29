get*normal*dense*chol*suff_stats(x::AbstractMatrix{<:Real})

密な共分散行列を持つ多変量正規分布の十分統計量を返します。サンプル共分散のコレスキー分解は「バイアスのある」バージョンであることに注意してください（n で割られ、n - 1 ではありません）。
