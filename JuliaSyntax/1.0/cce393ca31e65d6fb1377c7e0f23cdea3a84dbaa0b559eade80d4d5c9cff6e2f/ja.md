トークンの種類の文字列表現を返すか、種類が K"Identifier" のようなトークンのクラスを表す場合は `nothing` を返します。

`unique=true` の場合、種類が対応する入力トークンを一意に定義する場合のみ文字列を返し、それ以外の場合は `nothing` を返します。`unique=false` の場合は、種類の名前を返します。

TODO: `untokenize()` を `Base.string()` で置き換えますか？
