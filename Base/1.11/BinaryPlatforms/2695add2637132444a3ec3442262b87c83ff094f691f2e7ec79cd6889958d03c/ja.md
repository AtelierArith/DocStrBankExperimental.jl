```
os_version(p::AbstractPlatform)
```

この `Platform` オブジェクトによって決定されたOSバージョンを取得します。OSバージョンが強制されていない場合やデータが利用できない場合は `nothing` を返します。これは、プラットフォームSDKの断片化が高いMacOSやFreeBSDオブジェクトで最も一般的に使用され、特定のプラットフォームバージョンでのみ機能が利用可能です。
