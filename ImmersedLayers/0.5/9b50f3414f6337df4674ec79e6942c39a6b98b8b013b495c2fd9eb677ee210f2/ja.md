```
surface_velocity_in_translating_frame!(vel,x,base_cache,motions,t)
```

移動参照フレーム（`reference_body`キーワードで指定）で問題が設定されているときに表面速度を評価します。これは、参照体の平行移動速度を除去します。これは、自由流速度として適用されるため（符号が反転します）。
