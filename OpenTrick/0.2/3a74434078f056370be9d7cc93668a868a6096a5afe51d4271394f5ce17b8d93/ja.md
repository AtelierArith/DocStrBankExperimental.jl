```
opentrick(openfn[, args... [; <キーワード引数>]])
```

`openfn`を`(handlefn, args... ,kwargs ...)`を引数として呼び出し、`IOWrapper`インスタンスを返します。（注：`handlefn`は`opentrick`によって提供されます。）

# 引数

  * `openfn::Function` 実際に`IO`インスタンスを取得するために呼び出される関数。`openfn`は最初の引数として`Function(::IO)`インスタンスを受け取る必要があります。
  * `args` `openfn`に渡されるオプションの引数
  * `kwargs` `openfn`に渡されるオプションのキーワード引数

# 例

```jldoctest
julia> using OpenTrick

julia> filename = tempname();

julia> io = opentrick(open, filename, "w+");

julia> write(io, "hello world!")
12

julia> seek(io, 0);

julia> readline(io)
"hello world!"

```
