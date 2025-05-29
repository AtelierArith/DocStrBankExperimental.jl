```
注釈
```

# コンストラクタ

```julia
Annotation(;angle, content, point_at)
```

# キーワード引数

  * `angle::Real` は注釈のポインタの角度です。
  * `content::String` は注釈のテキスト内容です。
  * `point_at::Tuple{Real, Real}` は注釈が指すべき軸フレーム内の位置を指定します。典型的なものは `(1, 0)` で、これは注釈が軸フレームの南東の隅を指すことを意味します。
