```
MIME
```

標準的なインターネットデータ形式を表す型です。"MIME"は"Multipurpose Internet Mail Extensions"の略で、標準は元々電子メールメッセージへのマルチメディア添付ファイルを説明するために使用されていました。

`MIME`オブジェクトは、[`show`](@ref)の第二引数として渡すことができ、その形式での出力を要求します。

# 例

```jldoctest
julia> show(stdout, MIME("text/plain"), "hi")
"hi"
```
