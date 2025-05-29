```
CroppingOperator(outdims, inpdims, offset=defaultoffset(outdims,inpdims))
```

は、サイズ `inpdims` の配列をクロッピングしてサイズ `outdims` の配列を生成する線形マップを提供します。デフォルトでは、出力配列は入力配列に対して中心に配置されます（`fftshift` と同じ規則を使用）。オプションの引数 `offset` を使用すると、異なる相対位置を指定できます。`offset` が指定されている場合、マルチ次元インデックス `i` における出力値は、インデックス `j = i + offset` における入力値によって与えられます。

クロッピング演算子の随伴はゼロパディング演算子です。

参照: [`ZeroPaddingOperator`](@ref).
