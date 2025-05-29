```julia
File{T <: Any} <: Servable
```

  * name**::String**
  * path**::String**

`File` `Servable`は、`Connection`にファイルを書き込みます。`T`はファイルの拡張子を意味し、`.html`ファイルは`File{:html}`になります。ファイルのインデックスを取得すると、`File[]`はフィールドパスを返します。ファイルに対して`string`を使用すると、ファイルを`String`として読み取ります。

```julia
File(`dir`**::String**)
```

```example
# write! candidate
io = IOBuffer()

# make a file
myf::File{:jl} = File("myfiles/example.jl")
# writing
write!(io, myf)
```
