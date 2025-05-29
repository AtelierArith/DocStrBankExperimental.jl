```
@look ex
@look s[, k]
```

`look`のマクロバージョンは、シンボルに依存せずに変数にアクセスする便利な方法をサポートします。`@look s.a`と`@look s a`は、`look(s, :a)`と同じように動作します。

参照: [`look`](@ref)

# 例

```julia-repl
julia> "my system"
       @system S(Controller) begin
           "a param"
           a => 1 ~ preserve(parameter)
       end;

julia> @look S.a
[doc]
  a param

[code]
  a => 1 ~ preserve(parameter)
```
