パラメータ要件。構造体メンバーと関数パラメータの両方に適用されます。

要件の種類:

  * `OPTIONAL`: デフォルトのゼロ（またはnullptr）値を持つことができ、センチネル値として機能します（Juliaの`Nothing`に似ています）。
  * `REQUIRED`: 提供されなければならず、センチネル値は許可されません。
  * `POINTER_OPTIONAL`: nullである可能性のあるポインタですが、提供される場合は有効な要素を持っていなければなりません。
  * `POINTER_REQUIRED`: 有効なポインタでなければならず、その要素はオプションです（例: センチネル値を許可されます）。
  * `POINTER_FULLY_OPTIONAL`: nullであるか、オプションの要素を持つポインタである可能性があります（例: センチネル値を許可されます）。

```julia
primitive type PARAM_REQUIREMENT <: Enum{Int32} 32
```
