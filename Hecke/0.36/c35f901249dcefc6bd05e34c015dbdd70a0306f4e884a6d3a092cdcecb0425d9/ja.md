```
simplify(K::AbsSimpleNumField; canonical::Bool = false) -> AbsSimpleNumField, NumFieldHom{AbsSimpleNumField, AbsSimpleNumField}
```

より「単純な」定義多項式によって与えられる同型体 $L$ を見つけようとします。デフォルトでは、「単純」とはより小さい指数を持つことと定義され、テストは最大の整域の LLL 基底のみを使用して行われます。

`canonical` が `true` に設定されている場合、PARI の `polredabs` の定義を使用して、標準的な定義多項式が見つかります。この定義は http://beta.lmfdb.org/knowledge/show/nf.polredabs で説明されています。

両方のバージョンは、最大の整域の LLL 符号化基底を必要とします。
