```
check_valid_symmetry(pge::PeriodicGraphEmbedding{D,T}, t::SVector{D,T}, r=nothing, vtypes=nothing, issorted=false)
```

周期グラフ埋め込みが、`r`（`nothing`でない場合）によって回転され、その後`t`によって平行移動されたものと同一であることを確認します。`vtypes`が`nothing`でない場合、任意の頂点`x`は、`vtypes[x] == vtypes[y]`となるように頂点`y`にマッピングされなければなりません。`issorted`が設定され、`T <: Rational`の場合、より高速な二分法アプローチを使用するために`issorted(pge.pos)`を仮定します。

そうであれば、初期の頂点とその対称画像との間の`vmap`、および原点に対する各対称画像の`offsets`を返します。そうでなければ、`nothing`を返します。
