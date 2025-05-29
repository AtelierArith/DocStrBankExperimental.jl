```
tracyplot_config(name::String; format::Symbol=:number, step::Bool=false, fill::Bool=true, color::Union{Integer,Symbol,NTuple{3, Integer}, Nothing}=nothing)
```

指定された名前でプロットを構成します。通常、プロットごとに1回呼び出されるべきです。

  * `format` パラメータは `:number`、`:memory`、または `:percentage` のいずれかである必要があります。
  * `step` パラメータは、プロットが階段状に表示されるか、プロットポイント間で滑らかに変化するかを決定します。
  * `fill` パラメータは、プロットの下の領域を固体色で塗りつぶすことを無効にするために使用できます。

`color` が `nothing` の場合、デフォルトの色が使用されます。それ以外の場合、`color` 引数は次のように指定できます：

  * 整数：色の16進コード `0xRRGGBB`。
  * シンボル：`：black`、`：blue`、`：green`、`：cyan`、`：red`、`：magenta`、`：yellow`、`：white`、`：light_black`、`：light_blue`、`：light_green`、`：light_cyan`、`：light_red`、`：light_magenta`、`：light_yellow`、`：light_white` のいずれかの値を取ることができます。
  * 3つの整数のタプル：RGB値 `(R, G, B)` で、各値は 0..255 の範囲にあります。

参照： [`tracyplot`](@ref)。
