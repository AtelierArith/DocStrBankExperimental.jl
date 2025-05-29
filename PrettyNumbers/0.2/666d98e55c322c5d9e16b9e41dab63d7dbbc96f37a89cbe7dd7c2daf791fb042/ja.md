```
pretty_number([io::IO, | String, ]number::Number; backend, kwargs...) -> [Nothing | String]
```

`number`をきれいに表示します。

最初の引数が`io`の場合、数値はそれに出力されます。`String`の場合、表示された数値を含む文字列が返されます。省略された場合、デフォルトは`stdout`です。

数値は指定された`backend`を使用して表示されます。以下のオプションが利用可能です：

  * `Val(:latex)`: LaTeXバックエンド。
  * `Val(:text)`: テキストバックエンド。

# キーワード

これらはすべてのバックエンドで利用可能な一般的なキーワードです。各バックエンドは、以下のセクションに示すように、特定のキーワードのセットを定義しています。

すべてのキーワードは`number`の型に依存します。

## 有理数

`number`が`Rational`の場合、以下のキーワードが利用可能です：

  * `compact::Bool`: `true`の場合、有理数はコンパクトに1行で表示されます（例：`³/₄`）。そうでない場合、有理数は複数行で表示されます（**デフォルト** = `true`）：

```
    123
    ————
    4567
```

## 数値

それ以外の場合、`number`は10進法の科学的表記法を使用して表示されます。この場合、以下のキーワードが利用可能です：

  * `always_print_base::Bool`: `true`の場合、基数は常に表示されます。基数の指数が0の場合でも表示されます。（**デフォルト** = `false`）
  * `significand_format::String`: 有効数字を表示するために使用されるフォーマットで、`Printf.@printf`関数で説明されています。（**デフォルト** = `"%g"`）
  * `show_base::Bool`: `true`の場合、基数が表示されます。そうでない場合は省略されます。（**デフォルト** = `true`）
  * `show_significand::Bool`: `true`の場合、有効数字が表示されます。そうでない場合は省略されます。（**デフォルト** = `true`）
  * `new_decimal_base::Union{Nothing, Number}`: 数値の場合、数値の10進法の基数がこの数値に変換されます。`nothing`の場合、基数は変更されません。（**デフォルト** = `nothing`）

# テキストバックエンドのキーワード

## 数値

  * `multiplication_sign::Char`: 有効数字と10進法の基数の間に使用される乗算記号で、一般的なオプションは`'⋅'`と`'×'`です。（**デフォルト** = `'×'`）

# LaTeXバックエンドのキーワード

これらのキーワードはLaTeXバックエンドのみに適用され、すべてのサポートされている数値型に適用されます。

  * `math_env::Symbol`: `wrap_in_math_env`が`true`の場合、出力をラップする数学環境のタイプ。可能なオプションは、インラインLaTeX数学環境（`$`）のための`:inline`、または`egin{equation} .. nd{equation}`を使用するための`:equation`です。（**デフォルト**: `:inline`）
  * `wrap_in_math_env::Bool`: `true`の場合、出力は数学環境にラップされます。ユーザーは、キーワード`math_env`で関数が使用する環境を選択できます。（**デフォルト**: `false`）

## 数値

  * `multiplication_sign::Symbol`: 有効数字と10進法の基数の間に使用される乗算記号で、一般的なオプションは`\cdot`と`\times`です。（**デフォルト** = `"\times"`）

# 拡張ヘルプ

## 例

### テキストバックエンド

```julia
julia> pretty_number(19//86)
¹⁹/₈₆

julia> pretty_number(19//86; compact = false)
19
——
86

julia> pretty_number(1906.1896)
1.90619 × 10³

julia> pretty_number(1906.1896; significand_format = "%.10f")
1.9061896000 × 10³

julia> pretty_number(1906.1896; new_decimal_base = 4)
0.190619 × 10⁴
```

### LaTeXバックエンド

```julia
julia> pretty_number(19//86; backend = Val(:latex))
^{19}/_{86}

julia> pretty_number(19//86; backend = Val(:latex), compact = false)
\frac{19}{86}

julia> pretty_number(1906.1896; backend = Val(:latex))
1.90619 \times 10^{3}

julia> pretty_number(1906.1896; backend = Val(:latex), significand_format = "%.10f")
1.9061896000 \times 10^{3}

julia> pretty_number(1906.1896; backend = Val(:latex), new_decimal_base = 4)
0.190619 \times 10^{4}
```
