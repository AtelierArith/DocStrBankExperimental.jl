```
NWState(nw_or_nw_wrapper;
        utype=Vector{Float64}, ufill=filltype(utype),
        ptype=Vector{Float64}, pfill=filltype(ptype), default=true)
```

ネットワーク/ラッパー `nw` のための「空の」 `NWState` オブジェクトを作成します。フラットタイプ `utype` と `ptype` を持ちます。配列はそれぞれ `ufill` と `pfill` で事前に埋められます（デフォルトは NaN です）。

`default=true` の場合、ネットワークコンポーネントに付随するデフォルトの状態とパラメータ値がロードされます。
