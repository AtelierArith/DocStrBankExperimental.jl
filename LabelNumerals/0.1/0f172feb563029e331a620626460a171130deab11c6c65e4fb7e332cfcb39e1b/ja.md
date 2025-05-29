```
    LabelNumeral{T<:Integer}
```

`Integer` 型のラッパーで、以下の機能を提供します：

1. プレフィックス - A-1、A-2 など...
2. 小文字または大文字への変換
3. 表示および印刷オプション
4. `+, -, <=, ==, >, isless, max, min` のような数学演算子

ラップされた `struct` は以下のメソッドを実装する必要があります：

```
1. T(::String)
2. T(::Int)
3. Base.hash(::T)
4. Base.convert{S <: Integer}(::Type{S}, num::T)  <-- 標準の数値型に変換するため
```
