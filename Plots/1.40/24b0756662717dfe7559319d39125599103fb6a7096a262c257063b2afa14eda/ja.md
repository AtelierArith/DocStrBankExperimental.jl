既存のプロットからサブプロットを抽出する。

# 例

```julia-repl
julia> p1, p2 = plot(1:2), plot(10:20)
julia> pl = plot(p1, p2)  # 2つのサブプロットを含むプロット

julia> plot(pl.subplots[1])  # 1つ目のサブプロットをスタンドアロンプロットとして抽出
julia> plot(pl.subplots[2])  # 2つ目のサブプロットをスタンドアロンプロットとして抽出
```
