```
@mainname(file)
```

ファイルのメイン名を返します。つまり、最後のドットの前の部分と拡張子です。

# 例

```julia
julia> @mainname("~/test.xyz")
("test", "xyz")
```
