```
hardlink(src::AbstractString, dst::AbstractString)
```

既存のソースファイル `src` に名前 `dst` でハードリンクを作成します。宛先 `dst` は存在してはいけません。

関連情報: [`symlink`](@ref).

!!! compat "Julia 1.8"
    このメソッドは Julia 1.8 で追加されました。

