```
module Errors
```

エラータイプのインスタンスを含むために使用されるラッパーモジュールであり、パッケージの名前空間を汚染しません。

# 例

```jldoctest
julia> print(PAF.Errors.InvalidZero)
InvalidZero
```

関連情報: [`ParserException`](@ref)
