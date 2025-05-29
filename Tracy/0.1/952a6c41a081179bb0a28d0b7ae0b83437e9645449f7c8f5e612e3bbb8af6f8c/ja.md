```
tracymsg(msg::AbstractString; color::Union{Integer,Symbol,NTuple{3, Integer}, Nothing}=nothing, callstack_depth::Integer=0)
```

Tracyにメッセージを送信し、「メッセージ」ウィンドウに表示されます。`color`が`nothing`の場合、デフォルトの色が使用されます。それ以外の場合、`color`引数は次のように指定できます：

  * 整数：色の16進コードを`0xRRGGBB`として。
  * シンボル：値は`:black`、`:blue`、`:green`、`:cyan`、`:red`、`:magenta`、`:yellow`、`:white`、`:light_black`、`:light_blue`、`:light_green`、`:light_cyan`、`:light_red`、`:light_magenta`、`:light_yellow`、`:light_white`のいずれかを取ることができます。
  * 3つの整数のタプル：RGB値`(R, G, B)`で、各値は0..255の範囲内です。

`callstack_depth`引数は、収集されるコールスタックの深さを決定します。
