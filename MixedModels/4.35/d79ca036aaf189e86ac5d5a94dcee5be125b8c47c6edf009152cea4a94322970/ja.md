```
saveoptsum(io::IO, m::MixedModel)
saveoptsum(filename, m::MixedModel)
```

`m.optsum`（`lowerbd`フィールドなし）をJSON形式でIOストリームまたはファイルに保存します。

`lowerbd`フィールドを省略する理由は、それがしばしばJSONで許可されていない`-Inf`値を含むためです。
