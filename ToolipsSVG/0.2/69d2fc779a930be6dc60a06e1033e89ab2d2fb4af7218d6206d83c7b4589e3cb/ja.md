2023年2月に[chifi - an open source software dynasty.](https://github.com/orgs/ChifiSource)によって、[toolips](https://github.com/orgs/ChifiSource/teams/toolips)チームによって作成されました。このソフトウェアはMITライセンスです。

### ToolipsSVG

このモジュールは、さまざまなコンポーネントの配列を提供し、パスとの連携をより徹底的に行います。

###### exports

パスインターフェース

  * `M!`
  * `L!`
  * `Z!`
  * `Q!`
  * `C!`
  * `A!`

位置、形状、サイズ。

  * `size(::Component{<:Any})`
  * `set_size!`
  * `get_position`
  * `set_position!`
  * `get_shape`
  * `set_shape`

通常のコンポーネント

  * `text`
  * `path`
  * `image`
  * `circle`
  * `rect`
  * `line`
  * `ellipse`
  * `polygon`
  * `polyline`
  * `use`
  * `g`
  * `svg`
  * `div`
  * `tmd`

SVGシェイプ

  * `star`
  * `polyshape`
