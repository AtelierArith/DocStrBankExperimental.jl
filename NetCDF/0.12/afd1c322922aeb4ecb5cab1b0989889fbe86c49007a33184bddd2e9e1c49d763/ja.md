```
ncputatt(nc::String,varname::String,atts::Dict)
```

指定されたNetCDFファイル名 `nc` に対して、`atts` で定義された属性を変数 `varname` に書き込みます。既存の属性は上書きされます。varname が有効な変数名でない場合、グローバル属性が書き込まれます。
