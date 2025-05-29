```
map_expression(transform::Function, 
               expr::JuMP.AbstractJuMPScalar)::JuMP.AbstractJuMPScalar
```

`expr`の各変数が`transform`を介して変換される新しい式をマップして返します。これはユーザー拡張を書く際に役立ちます。
