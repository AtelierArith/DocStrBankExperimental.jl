```
activate!(arch::SingleDeviceArchitecture; priority=:normal)
```

指定されたデバイス上で指定されたアーキテクチャをアクティブにし、バックエンドの優先度を設定します。優先度として受け入れられる値は `:normal`、 `:low`、および `:high` です。
