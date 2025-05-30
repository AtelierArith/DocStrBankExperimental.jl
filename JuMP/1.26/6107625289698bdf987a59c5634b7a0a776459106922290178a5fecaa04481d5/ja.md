```
AbstractJuMPScalar <: MutableArithmetics.AbstractMutable
```

すべてのスカラー型のための抽象基底型

`AbstractMutable`のサブタイピングは、いくつかの`Base`関数の呼び出しを、型昇格をより慎重に処理するMAのメソッドにリダイレクトできるようにします（たとえば、SparseArraysにおけるスパース行列積の昇格は通常JuMP型には機能しません）および`AffExpr`と`QuadExpr`の可変性を利用します。
