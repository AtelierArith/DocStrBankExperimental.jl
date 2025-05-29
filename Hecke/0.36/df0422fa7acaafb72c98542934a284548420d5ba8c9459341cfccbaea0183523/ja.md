```
fixed_field(K::SimpleNumField,
            sigma::Map;
            simplify::Bool = true) -> number_field, NumFieldHom{AbsSimpleNumField, AbsSimpleNumField}
```

与えられた数体 $K$ と $K$ の自己同型 $\sigma$ に対して、この関数は $\sigma$ の不変体を数体 $L$ と $K$ への $L$ の埋め込み $i$ からなるペア $(L, i)$ として返します。

デフォルトでは、この関数は $L$ の小さな定義多項式を見つけようとします。これは `simplify = false` に設定することで無効にできます。
