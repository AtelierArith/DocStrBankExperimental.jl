```
perform_method!(scheduler, method, solution; delayed_success=false)::Result
```

与えられた解に対してメソッドを実行し、`Results`オブジェクトを返します。

また、現行の解、反復回数、およびメソッドの統計を`method*stats`に更新します。さらに、終了条件をチェックし、最終的に返された`Results`オブジェクトの`terminate`を設定します。`delayed*success`の場合、成功は即座には決定されず、統計はそれに応じて更新されますが、`delayed*success*update`の後の呼び出しで行われます。
