```
hasext(path, ext::String) -> Bool
hasext(path, exty::Symbol) -> Bool
```

パスの拡張子をチェックします。文字列は拡張子と正確に一致する必要があります：

```julia
julia> hasext("myfile.txt", "txt")
true

julia> hasext("myfile.TXT", "txt")
false
```

シンボルは拡張子グループに一致し、大文字と小文字を区別しません：

```julia
julia> hasext("myfile.jpeg", :jpeg)
true

julia> hasext("myfile.jpg", :jpeg)
true

julia> hasext("myfile.JPEG", :jpeg)
true

julia> hasext("myfile.jpeg", :jpg)  # 拡張子グループの任意の拡張子は、そのグループのシンボルとして機能します
true
```

`exty` も参照してください。
