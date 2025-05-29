```
setlights(B, Dict("on" => true))
setlights(B, Dict("on" => false))
setlights(B, Dict("on" => true, "sat" => 123, "bri" => 243, "hue" => 123)
```

グループ内のすべてのライトを設定するには、設定の辞書を渡します。

例えば Dict{Any,Any}("on" => true, "sat" => 123, "bri" => 123, "hue" => 123) のように、"hue" は 0 から 65535 の範囲です (？)、"sat" と "bri" はそれぞれ彩度と明るさで、1 から 254 の範囲です。0 は赤、黄色は 12750、緑は 25500、青は 46920 などです。

キーが省略された場合、そのライトのその側面は変更されません。

キーは AbstractStrings であり、値は数値で、AbstractStrings に変換されます。
