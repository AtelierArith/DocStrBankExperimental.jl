```
TorObj
```

単一の一般的なTORオブジェクトを含む構造体。

## フィールド

  * `name::String`: TORオブジェクトの名前。例: "my_rim"。
  * `objtype::String`: TORオブジェクトのタイプ。例: "tabulated*rim*xy"。
  * `propname::Vector{String}`: オブジェクトプロパティの名前。例:  ["file*name", "unit", "number*of*points", "translation", "polar*origin"]
  * `propval::Vector{String}`: `propnames`の名前に対応するオブジェクトプロパティの値。例: ["h*9m*scalloped_rim.xyz", "in", "112", "struct(x: 0.0 in, y: 0.0 in)",  "struct(status: automatic, x: 0.0 in, y: 0.0 in)"]

`propval`の「値」は、存在する可能性のある数値を解析する必要がある単なる文字列であることに注意してください。

## 参照

  * `parse_tor_struct`
