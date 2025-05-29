```
any_problems(ts)
```

テストセットをチェックして、問題（`Error`または`Fail`）があったかどうかを確認します。`DefaultTestSet`とは異なり、`ReportingTestSet`は失敗時に例外をスローしません。したがって、ランナーコードから終了コードを設定するために、`exit(any_problems(top_level_testset))`を使用して確認します。
