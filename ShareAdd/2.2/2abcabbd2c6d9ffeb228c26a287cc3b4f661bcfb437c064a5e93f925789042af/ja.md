```
@showenv
@showenv item
```

デスクトップGUIでオープン（共有）環境フォルダーを開きます。このマクロの利点は、これらのフォルダーが隠しフォルダー ~/.julia/ にあるため、OSでアクセスするのが難しい場合があるのに対し、簡単にアクセスできるようにすることです。

このマクロはエクスポートされています。

# 例

```julia-repl
julia> @showenv # 引数なしで呼び出すと、すべての共有環境を含む「environments」フォルダーが開きます
julia> @showenv Revise # Reviseパッケージを含む環境フォルダーを開きます
julia> @showenv "Revise" # 引数の引用符付きと引用符なしの形式の両方がOKです
julia> @showenv Math # 共有環境 @Math のフォルダーを開きます
```
