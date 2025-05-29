```
timdef(action, item, value="")
```

カレンダー入力文字列に関連付けられたデフォルトを設定および取得します。

### 引数

  * `action`: 実行するアクションの種類、`:SET` または `:GET`
  * `item`: 興味のあるデフォルト項目。リクエスト可能な項目は次のとおりです：

      * `:CALENDAR` の許可される値：

          * `"GREGORIAN"`
          * `"JULIAN"`
          * `"MIXED"`
      * `:SYSTEM` の許可される値：

          * `"TDB"`
          * `"TDT"`
          * `"UTC"`
      * `:ZONE` の許可される値（`0 <= HR < 13` および `0 <= MN < 60`）：

          * `"EST"`
          * `"EDT"`
          * `"CST"`
          * `"CDT"`
          * `"MST"`
          * `"MDT"`
          * `"PST"`
          * `"PDT"`
          * `"UTC+$HR"`
          * `"UTC-$HR"`
          * `"UTC+$HR:$MN"`
          * `"UTC-$HR:$MN"`

### 出力

デフォルト項目に関連付けられた値を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/timdef_c.html)
