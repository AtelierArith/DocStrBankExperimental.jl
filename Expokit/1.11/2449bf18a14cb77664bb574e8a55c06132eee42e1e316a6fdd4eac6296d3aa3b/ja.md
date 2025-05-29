```
padm(A; p=6)
```

行列指数をPade近似を使用して計算します。

`padm`は、指数関数に対する既約の(p, p)次数の有理Pade近似を使用します。結果は常に密な行列です。

# 入力

  * `A` – 密または疎の行列
  * `p` – （オプション、デフォルト: 6）指数関数に対する有理Pade近似の次数

# 注意事項

このJulia実装は、Roger B. SidjeによるExpokitのPADM Matlabコードに由来します。以下を参照してください。

---

E = padm( A, p )   PADMは、指数関数に対する既約の(p,p)次数の有理Pade近似を使用して行列指数exp(A)を計算します。

E = padm( A )   pは内部的に6に設定されます（推奨され、一般的に満足のいく結果です）。

CHBV、EXPOKIT、およびMATLABが提供する関数EXPMおよびEXPM1も参照してください。

Roger B. Sidje (rbs@maths.uq.edu.au)   EXPOKIT: 行列指数を計算するためのソフトウェアパッケージ。   ACM - Transactions On Mathematical Software, 24(1):130-156, 1998
