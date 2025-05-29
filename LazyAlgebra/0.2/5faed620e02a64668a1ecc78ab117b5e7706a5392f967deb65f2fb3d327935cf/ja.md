```
vmul(A, x) -> y
```

は `y = A*x` を生成します。デフォルトの動作は `apply(Direct,A,x,false)` を呼び出すことです。メソッド [`vmul!`](@ref) はインプレースバージョンです。
