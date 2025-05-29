```
HostPlatform()
```

現在のホストシステムに対応する `Platform` オブジェクトを返し、すべての関連する比較戦略がホストプラットフォームモードに設定されます。これは次のことと同等です：

```
HostPlatform(parse(Platform, Base.BinaryPlatforms.host_triplet()))
```
