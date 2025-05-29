```
setlight(B, 1, Dict("on" => true))
setlight(B, 3, Dict("on" => false))
setlight(B, 2, Dict("on" => true, "sat" => 123, "bri" => 243, "hue" => 123)
```

辞書の設定を渡すことでライトを設定します。

例えば Dict{Any,Any}("on" => true, "sat" => 123, "bri" => 123, "hue" => 123) のように、"hue" は 0 から 65535 の範囲で、"sat" と "bri" はそれぞれ 1 から 254 の範囲の彩度と明るさです。0 は赤、黄色は 12750、緑は 25500、青は 46920 などです。

キーが省略された場合、そのライトのその側面は変更されません。

キーは AbstractStrings であり、値は数値で、AbstractStrings に変換されます。
