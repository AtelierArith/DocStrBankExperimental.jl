```
closewrite(stream)
```

フルデュプレックスI/Oストリームの書き込み半分をシャットダウンします。最初に[`flush`](@ref)を実行します。基盤となるファイルにデータがこれ以上書き込まれないことを他の端に通知します。これはすべてのIOタイプでサポートされているわけではありません。

# 例

```jldoctest
julia> io = Base.BufferStream(); # これはブロックしないので、同じタスクで読み書きできます

julia> write(io, "request");

julia> # ここで`read(io)`を呼び出すと永遠にブロックします

julia> closewrite(io);

julia> read(io, String)
"request"
```
