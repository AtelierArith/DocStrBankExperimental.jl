```
label2ind(label, encoding) -> Int
```

与えられた `label` をエンコーディングによって定義された対応するインデックスに変換します。バイナリの場合、正のラベルはインデックス `1` を、負のラベルはインデックス `2` をそれぞれ返すことに注意してください。

```
julia> label2ind(:no, LabelEnc.NativeLabels([:yes,:no]))
2

julia> label2ind(1, LabelEnc.MarginBased())
1

julia> label2ind(-1, LabelEnc.MarginBased())
2
```
