```
ZeroPaddingOperator(outdims, inpdims, offset=defaultoffset(outdims,inpdims))
```

は、サイズ `inpdims` の配列をゼロパディングしてサイズ `outdims` の配列を生成する線形写像を生成します。デフォルトでは、入力配列は出力配列に対して中心に配置されます（`fftshift` と同じ規則を使用）。オプションの引数 `offset` を使用して、異なる相対位置を指定することができます。`offset` が指定されている場合、マルチディメンションインデックス `j` の入力値は、結果のインデックス `i = j + offset` にコピーされます。

ゼロパディングオペレーターは、クロッピングオペレーターの随伴として実装されています。

参照: [`CroppingOperator`](@ref).
