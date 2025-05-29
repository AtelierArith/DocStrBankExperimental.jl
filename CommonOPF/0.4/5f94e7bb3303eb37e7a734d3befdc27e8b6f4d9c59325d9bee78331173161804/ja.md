```
remove_bus!(j::String, net::Network{MultiPhase})
```

バス `j` をモデルから削除し、バス i->k からの同等のラインを作成します。i->j および j->k からの導体がインピーダンス行列を持っていると仮定します。
