```
lincom(r::AbstractDIDResult, linmap::AbstractMatrix{<:Real}, subset=nothing)
```

DID結果`r`からの係数推定値を行列`linmap`を通じて線形変換します。`linmap`の列数は`r`からの係数の総数と一致しなければなりません。`linmap`が正方行列でない場合（列数より行数が少ない場合）、変換後に残る係数を表すインデックスを指定するために`subset`を指定する必要があります。詳細は[`rescale`](@ref)を参照してください。
