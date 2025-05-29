```
platform_dlext(p::AbstractPlatform = HostPlatform())
```

指定されたプラットフォームの動的ライブラリ拡張子を返します。デフォルトでは、現在実行中のプラットフォームが使用されます。例えば、Linuxベースのプラットフォームの場合は「so」、Windowsベースのプラットフォームの場合は「dll」などが返されます...
