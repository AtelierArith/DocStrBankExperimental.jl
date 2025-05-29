```
git()
```

Gitを実行するための`Cmd`を返します。

## 例

```julia
julia> run(`$(git()) clone https://github.com/JuliaRegistries/General`)
```

これは、明示的に分割された引数を使って次のように書くこともできます。

```
julia> run(git(["clone", "https://github.com/JuliaRegistries/General"]))
```

コマンド文字列の解析を回避するためです。
