```
NWParameter(nw_or_nw_wraper;
            ptype=Vector{Float64}, pfill=filltype(ptype), default=true)
```

ネットワーク/ラッパー `nw` のための "空" `NWParameter` オブジェクトを作成します。フラットタイプ `ptype` を持ちます。配列は `pfill` で事前に埋められます（デフォルトは NaN です）。

`default=true` の場合、ネットワークコンポーネントに付随するデフォルトパラメータ値が読み込まれます。
