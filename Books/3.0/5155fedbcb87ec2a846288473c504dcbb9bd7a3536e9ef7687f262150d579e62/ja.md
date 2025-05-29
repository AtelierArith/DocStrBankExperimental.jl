```
sco(
    expr::AbstractString;
    pre::Function=identity,
    process::Union{Nothing,Function}=nothing,
    post::Function=identity
)
```

`expr`に対してコードと出力を示します。出力は、`pre`、`process`、または`post`を適用することによって処理されます。具体的には、

  * `pre`は`convert_output`の前に適用されます
  * `process`は`convert_output`の代わりに適用されます
  * `post`は`convert_output`の後に適用されます

例えば、次のようにします。

```julia
let
    pre(out) = Options(out; label="l")
    post = string
    sco("DataFrame(x = [1])"; pre, post)
end
```

この場合、DataFrameは3つの段階を経ます：

1. `pre`がオブジェクトにラベル「l」を追加します
2. `process`は何もないので、`convert_output`は通常の処理を行い、DataFrameオブジェクトをMarkdownに変換します。
3. `post`は出力を文字列に変換します（この場合、`convert_output`によってすでに行われていますが）。

したがって、`convert_output`を無効にするには、`process=nothing`または`process=identity`を渡します。
