```julia
# single-line:
TextField(default="", placeholder=nothing)

# with specified size:
TextField(size; default="", placeholder=nothing)
```

テキスト入力 - ユーザーはテキストを入力でき、テキストは `@bind` を介して `String` として返されます。

# キーワード引数

  * `default`: 初期値
  * `placeholder`: テキスト入力が空のときに表示される値

# `size` 引数

  * `size` がタプル `(cols::Integer, row::Integer)` の場合、指定された寸法の **マルチライン** `<textarea>` が表示されます。
  * `size` が整数の場合、シングルライン入力の **幅** を制御します。

# 例

```julia
@bind author TextField()
```

```julia
@bind poem TextField((30,5); default="Hello\nJuliaCon!")
```
