```
savevalues!(integrator::DEIntegrator,
  force_save=false) -> Tuple{Bool, Bool}
```

現在の時間点または適切な場合に補間を使用して`saveat`ポイントで状態および時間変数を保存しようとします。戻り値はタプル`(saved, savedexactly)`です。`savevalues!`が値を保存した場合、`saved`はtrueになり、`savevalues!`が現在の時間点で保存した場合、`savedexactly`はtrueになります。

保存の優先順位/順序は次のとおりです：

  * `save_on`

      * `saveat`
      * `force_save`
      * `save_everystep`
