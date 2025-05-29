```
ParameterBounds(ids::Vector{Integer},lbs::Vector{Number},ubs::Vector{Number})
```

parameters[ids] は lbs と ubs の範囲内でなければならず、lbs と ubs は ids と同じサイズの配列です。最小限の干渉曲線が描けるパラメータ空間に対してハードバウンドを作成します。曲線の進化は、バウンドに達した場合に終了します。
