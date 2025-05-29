```
perform_method_pair!(scheduler, destroy, repair, sol)
```

与えられた解に対して破壊/修復メソッドペアを実行し、`Results`構造体を返します。

また、現行解、反復回数、およびメソッドの統計をmethod_statsに更新します。さらに、終了条件をチェックし、最終的に返された`Results`構造体のterminateを設定します。
