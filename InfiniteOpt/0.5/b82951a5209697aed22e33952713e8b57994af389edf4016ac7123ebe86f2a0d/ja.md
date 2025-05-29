```
map_dual(cref::InfOptConstraintRef, key::Val{ext_key_name}, result::Int; 
         kwargs...)
```

`cref`の双対を、拡張キー`key`によって区別される最適化モデルタイプの対応物にマップします。この`key`は`Val{ext_key_name}`として扱われます。ここで、`ref`は変数参照と制約参照の両方のメソッドを参照する必要があります。これは、元の無限形式において変数と/または制約の間に直接的なマッピングがない再定式化拡張のためにのみ定義する必要があります。そうでなければ、`optimizer_model_variable`と`optimizer_model_constraint`がデフォルトでこれらのマッピングを行うために使用され、`kwargs`も渡されます。ここで`result`は、`dual`で使用される結果インデックスです。
