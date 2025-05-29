```julia
write!(io, args ...) -> _
```

`write` `Function` は `<: IO` または `String` に `Servables` を `write!` するために使用されます。

```julia
write!(io::IO, servables::Servable ...) -> ::Nothing
write!(io::String, servables::Servable ...) -> ::String
```

```julia
using ToolipsServables
# 書き込み候補
str_sample = ""
buff = IOBuffer()

# テンプレーティング
mycomp = div("example", align = "center")

# 書き込み
write!(buff, mycomp)
str_sample = write!(str_sample, mycomp)
```

```example
# ファイルへの書き込み
file::File{:txt} = File("texts/example.txt")

rawfile = write!("", file)
```
