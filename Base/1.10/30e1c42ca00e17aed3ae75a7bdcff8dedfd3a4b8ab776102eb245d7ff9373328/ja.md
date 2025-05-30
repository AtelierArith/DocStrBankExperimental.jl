```
@cmd str
```

`str` 文字列から実行されるシェルコマンドを表す `Cmd` を生成します。[`Cmd`](@ref) オブジェクトはプロセスとして実行でき、生成した Julia プロセスを超えて生存することができます（詳細は `Cmd` を参照してください）。

# 例

```jldoctest
julia> cm = @cmd " echo 1 "
`echo 1`

julia> run(cm)
1
Process(`echo 1`, ProcessExited(0))
```
