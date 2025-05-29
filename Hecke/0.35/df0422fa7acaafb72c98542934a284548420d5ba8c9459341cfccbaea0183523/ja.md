```
fixed_field(K::SimpleNumField,
            sigma::Map;
            simplify::Bool = true) -> number_field, NumFieldHom{AbsSimpleNumField, AbsSimpleNumField}
```

数体 $K$ と $K$ の自己同型 $\sigma$ が与えられたとき、この関数は $\sigma$ の不変体を数体 $L$ と $K$ への埋め込み $i$ からなる対 $(L, i)$ として返します。

デフォルトでは、この関数は $L$ の小さな定義多項式を見つけようとします。これは `simplify = false` に設定することで無効にできます。
