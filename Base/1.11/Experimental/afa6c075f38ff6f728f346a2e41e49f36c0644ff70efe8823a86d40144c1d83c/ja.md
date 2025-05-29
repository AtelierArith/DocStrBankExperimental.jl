```
Base.Experimental.@MethodTable name
```

現在のモジュールに新しいMethodTableを作成し、`name`にバインドします。このメソッドテーブルは、[`Base.Experimental.@overlay`](@ref)マクロと共に使用して、関数のメソッドを定義することができ、グローバルメソッドテーブルに追加することなく使用できます。
